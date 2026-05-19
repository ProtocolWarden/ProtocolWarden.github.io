# CritiqueExecutor

**Role:** Owned execution backend — adversarial and reflexion critique loops
**GitHub:** [ProtocolWarden/CritiqueExecutor](https://github.com/ProtocolWarden/CritiqueExecutor)
**License:** AGPL-3.0-or-later

## What It Does

CritiqueExecutor runs iterative critique loops for AI task refinement.

**Topologies:**
- **Adversarial**: proposer (Claude Code) generates output; critic (Anthropic API) reviews in strict isolation; proposer revises until ACCEPT or round limit
- **Reflexion**: agent (Claude Code) executes; independent critic grades against criteria; agent receives only the rejection reason (never critic identity)

## Invariants

- `max_rounds` hard-capped at 10 (enforced in `CritiqueConfig.__post_init__`)
- Critic isolation: agent/proposer identity never reaches the critic prompt
- Topology routing: only `adversarial` and `reflexion` — no fallback topology

## New Capability

This is a new executor with no direct predecessor. It provides critique-driven quality enforcement that was previously unavailable in the platform.

## Dependencies

- [RxP](rxp.md) — RuntimeInvocation/RuntimeResult contract
- [CxRP](cxrp.md) — BackendName vocabulary
