# TeamExecutor

**Role:** Owned execution backend — multi-agent team coordination
**GitHub:** [ProtocolWarden/TeamExecutor](https://github.com/ProtocolWarden/TeamExecutor)
**License:** AGPL-3.0-or-later

## What It Does

TeamExecutor orchestrates a coordinator → worker → verifier team pattern for multi-stage AI task execution.

- **Coordinator** (Anthropic API): breaks the goal into stages, plans execution
- **Workers** (Claude Code subprocess): execute each stage against the repo
- **Verifier** (Anthropic API): grades each stage before proceeding; can REJECT to trigger retry

tiktoken-gated summarization fires when accumulated context exceeds threshold.

## Invariants

- **D1**: `goal_text` from the ExecutionRequest reaches worker subprocesses verbatim — no wrapping, no rewriting
- Verifier verdicts are ACCEPT or REJECT — no partial states
- Max cycles per stage are bounded by configuration

## Replaces

Replaces the `kodo` external integration (retired 2026-05-18, ADR 0005).

## Dependencies

- [RxP](rxp.md) — RuntimeInvocation/RuntimeResult contract
- [CxRP](cxrp.md) — BackendName vocabulary
