# TeamExecutor

**Role:** Owned execution backend — multi-agent team coordination
**GitHub:** [ProtocolWarden/TeamExecutor](https://github.com/ProtocolWarden/TeamExecutor)
**License:** AGPL-3.0-or-later

## What It Does

TeamExecutor orchestrates a coordinator → worker → verifier team pattern for multi-stage AI task execution.

- **Coordinator** (Claude Code subprocess): breaks the goal into stages, plans execution
- **Workers** (Claude Code or Codex CLI subprocess): execute each stage against the repo
- **Verifier** (Claude Code subprocess): grades each stage before proceeding; can REJECT to trigger retry

tiktoken-gated summarization fires when accumulated context exceeds threshold.

## Stage Primitives

Each `GoalStage` supports optional primitives that compose to build safe, verifiable execution:

| Primitive | Field | What it does |
|-----------|-------|--------------|
| Worktree isolation | `persist_changes: true` | Stage runs in an isolated git worktree; changes are cherry-picked back on success, discarded on failure |
| Scripted verification | `verification: [QuickCheck, ...]` | Runs commands with expected exit codes before calling agent verifiers; fast-path to reject broken stages |
| Adaptive advisor | `TeamConfig.adaptive_advisor` | After each sequential stage, coordinator LLM decides: continue / done (stop early) / add_stage (inject new stage) |
| Auto-commit | `TeamConfig.auto_commit` | Commits working directory after each successful sequential stage |

## Worker Backend

`worker_backend` selects the CLI used for worker and verifier subprocesses:

- `claude_code` (default) — `claude --message … --output-format json`
- `codex_cli` — `codex --approval-mode full-auto -q …`

Backend is propagated from the SwitchBoard `LaneDecision.metadata["worker_backend"]` → OperationsCenter adapter → TeamExecutor.

## Subprocess Safety

All subprocess calls use `core_runner.process.safe_run()`:

- `start_new_session=True` — child owns its own process group
- `os.killpg(SIGKILL)` on timeout — kills full descendant tree, not just direct child
- Transient SIGTERM handler — child group reaped if supervisor is killed

## Invariants

- **D1**: `goal_text` from the ExecutionRequest reaches worker subprocesses verbatim — no wrapping, no rewriting
- Verifier verdicts are ACCEPT or REJECT — no partial states
- Max cycles per stage are bounded by configuration
- Worktree isolation: failed stages leave no partial changes in the main working directory

## Replaces

Replaces the `kodo` external integration (retired 2026-05-18, ADR 0005).

## Dependencies

- [CoreRunner](corerunner.md) — `safe_run()` subprocess primitive
- [RxP](rxp.md) — RuntimeInvocation/RuntimeResult contract
- [CxRP](cxrp.md) — BackendName vocabulary
