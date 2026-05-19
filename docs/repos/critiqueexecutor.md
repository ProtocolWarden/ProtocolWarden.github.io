# CritiqueExecutor

**Role:** Owned execution backend — adversarial and reflexion critique loops
**GitHub:** [ProtocolWarden/CritiqueExecutor](https://github.com/ProtocolWarden/CritiqueExecutor)
**License:** AGPL-3.0-or-later

## What It Does

CritiqueExecutor runs iterative critique loops for AI task refinement.

**Topologies:**

- **Adversarial**: proposer (Claude Code or Codex CLI subprocess) generates output; critic reviews in strict isolation; proposer revises until ACCEPT or round limit
- **Reflexion**: agent executes; independent critic grades against criteria; agent receives only the rejection reason (never critic identity)

## Worker Backend

`worker_backend` selects the CLI used for proposer/agent subprocesses:

- claude_code (default) — `claude --message … --no-auto-commits --output-format json`
- codex_cli — `codex --approval-mode full-auto -q …`

The critic always receives only the prompt and verdict JSON — never the backend identity.

## Subprocess Safety

All subprocess calls use `core_runner.process.safe_run()`:

- `start_new_session=True` — child owns its own process group
- `os.killpg(SIGKILL)` on timeout — kills full descendant tree
- Timeout returns `{"status": "reject", "reason": "critic timed out"}` rather than raising

## Invariants

- `max_rounds` hard-capped at 10 (enforced in `CritiqueConfig.__post_init__`)
- Critic isolation: agent/proposer identity never reaches the critic prompt
- Topology routing: only `adversarial` and `reflexion` — no fallback topology

## New Capability

This is a new executor with no direct predecessor. It provides critique-driven quality enforcement that was previously unavailable in the platform.

## Dependencies

- [CoreRunner](corerunner.md) — `safe_run()` subprocess primitive
- [RxP](rxp.md) — RuntimeInvocation/RuntimeResult contract
- [CxRP](cxrp.md) — BackendName vocabulary
