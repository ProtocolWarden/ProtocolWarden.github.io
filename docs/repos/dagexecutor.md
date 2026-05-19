# DAGExecutor

**Role:** Owned execution backend — DAG-based workflow executor
**GitHub:** [ProtocolWarden/DAGExecutor](https://github.com/ProtocolWarden/DAGExecutor)
**License:** AGPL-3.0-or-later

## What It Does

DAGExecutor drives multi-node AI task graphs with topological scheduling and concurrent layer execution.

**Node types:**

| Node | What it does |
|------|-------------|
| `agent` | Claude Code or Codex CLI subprocess — receives `goal_text` verbatim |
| `bash` | Shell command (no shell features — list-form exec via `safe_run`) |
| `script` | Python script written to a temp file and executed |
| `loop` | Static poll (repeat until stdout contains `DONE`) or dynamic fan-out (one run per item, concurrent) |
| `gate` | Human file-based approval — advances (`approved`) or halts (`rejected`) |

**Graph engine:** [rustworkx](https://github.com/Qiskit/rustworkx) — Rust-backed DAG with cycle detection, topological sort, and layer-based concurrent execution via ThreadPoolExecutor.

## Worker Backend

`worker_backend` selects the CLI used for agent nodes:

- `claude_code` (default) — `claude --message … --output-format json --no-auto-commits`
- `codex_cli` — `codex --model … --approval-mode full-auto -q …`

Agent node commands are built as `list[str]` directly — no shell quoting or string construction.

## Subprocess Safety

All subprocess calls use `core_runner.process.safe_run()`:

- `start_new_session=True` — child owns its own process group
- `os.killpg(SIGKILL)` on timeout — kills full descendant tree
- No `shell=True` — commands are list-form; string commands split via `shlex.split()`

## Invariants

- **D1**: `goal_text` reaches agent nodes verbatim (node command appended as `--append-system-prompt`)
- Cycle detection fires before execution; malformed graphs are rejected at load time
- Gate nodes can only advance (`approved`) or halt (`rejected`) — no silent pass-through

## Replaces

Replaces the `Archon` external integration (retired 2026-05-18, ADR 0005).

## Dependencies

- [CoreRunner](corerunner.md) — `safe_run()` subprocess primitive
- [RxP](rxp.md) — RuntimeInvocation/RuntimeResult contract
- [CxRP](cxrp.md) — BackendName vocabulary
