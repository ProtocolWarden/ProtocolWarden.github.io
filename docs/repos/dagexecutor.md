# DAGExecutor

**Role:** Owned execution backend — DAG-based workflow executor
**GitHub:** [ProtocolWarden/DAGExecutor](https://github.com/ProtocolWarden/DAGExecutor)
**License:** AGPL-3.0-or-later

## What It Does

DAGExecutor drives multi-node AI task graphs with topological scheduling and concurrent layer execution.

**Node types:** `agent` (Claude Code subprocess), `bash` (shell), `script` (file-based), `loop` (static poll or dynamic fan-out), `gate` (human file-based approval)

**Graph engine:** [rustworkx](https://github.com/Qiskit/rustworkx) — Rust-backed DAG with cycle detection, topological sort, and layer-based concurrent execution via ThreadPoolExecutor.

## Invariants

- **D1**: `goal_text` reaches agent nodes verbatim (node command appended as `--append-system-prompt`)
- Cycle detection fires before execution; malformed graphs are rejected at load time
- Gate nodes can only advance (`approved`) or halt (`rejected`) — no silent pass-through

## Replaces

Replaces the `Archon` external integration (retired 2026-05-18, ADR 0005).

## Dependencies

- [RxP](rxp.md) — RuntimeInvocation/RuntimeResult contract
- [CxRP](cxrp.md) — BackendName vocabulary
