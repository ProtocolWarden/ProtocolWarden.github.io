# Spec Director Refactor

How OperationsCenter's `spec_director` was decomposed so that **every LLM call
goes through the backend executor** — closing audit, lifecycle, and provenance
gaps that direct-Claude code paths had left open.

Canonical decision record: OperationsCenter ADR 0007.

## Context

`spec_director` was a single watcher containing three Claude-bypassing paths
(board hygiene, campaign generation, phase orchestration). Two of them called
Claude directly, skipping model-binding policy, rate limiting, retry, the audit
trail, and lifecycle capture — a generated spec just appeared on disk with no
`run_id` provenance.

## Decision

Fold all LLM-needing operations through the normal
`Plane task → board_worker → ExecutionCoordinator → backend` pipeline. Split the
non-LLM operations into focused watchers that **emit Plane tasks** instead of
executing work themselves.

| Concern | Owner | LLM? |
|---|---|---|
| Hygiene (archive, bootstrap, auto-promote, recovery) | `spec_hygiene` watcher | No |
| Trigger detection (drop-file, queue-drain) | `spec_trigger` watcher | No |
| Spec generation execution | `board_worker` via `spec-author` task-kind | Yes (via backend) |
| Phase orchestration LLM step | Same `spec-author` handler, `task_phase` label | Yes (via backend) |

## Architecture

```mermaid
flowchart TD
    Plane["<b>Plane</b><br/>source of truth for all task state"]

    Trigger["<b>spec_trigger</b> (watcher)<br/>drop-file · queue-drain<br/>on fire: creates Plane task<br/>(kind: spec-author)"]
    Hygiene["<b>spec_hygiene</b> (watcher)<br/>archive · bootstrap · auto-promote<br/>recovery · phase-advance detection<br/>rebuilds active.json projection<br/>on phase-advance: creates Plane task<br/>(kind: spec-author, task_phase)"]
    OConsole["<b>OperatorConsole</b><br/>watcher_status reads<br/>active.json projection"]

    Worker["<b>board_worker</b><br/>picks up spec-author task<br/>planning → execute<br/>→ ExecutionCoordinator<br/>→ cl_dispatch_wrap<br/>→ backend writes file, commits, pushes<br/>→ RunArtifactWriter<br/>→ _handle_success: opens spec,<br/>creates campaign sub-tasks"]

    Trigger -- "creates task" --> Plane
    Hygiene -- "creates task / transitions" --> Plane
    Plane -- "reads" --> Hygiene
    Hygiene -- "writes active.json" --> OConsole
    Plane -- "spec-author task" --> Worker
    Worker -- "commits spec, campaign tasks" --> Plane
```

## Key invariants

- **All LLM calls go through the backend executor.** `_claude_cli.py` is
  deleted; a CI grep guard prevents reintroduction.
- **Plane is single-source-of-truth for task state.**
  `state/campaigns/active.json` is a Plane-derived projection rebuilt by
  `spec_hygiene` each cycle; OperatorConsole reads it (single writer).
- **Audit trail is end-to-end closed:** the spec file embeds
  `generated_by_run: <run_id>`, campaign sub-tasks carry `parent_run`, and
  `run_metadata.json` records `spec_slug` for `spec-author` tasks — any spec
  traces back to its execution.

## Related

- Sync & Data Transport — the same manifest-as-authority and shim-contract
  patterns recur there.
