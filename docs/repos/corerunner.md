# CoreRunner

!!! note "Rename in progress"
    This repo is being renamed from `ExecutorRuntime` → `CoreRunner` per
    ADR 0006. The GitHub repo, package name (`executor_runtime` → `core_runner`),
    and class name (`ExecutorRuntime` → `CoreRunner`) are all changing as part
    of the same work order.

## Mission

Canonical subprocess safety layer for the ProtocolWarden ecosystem. A Python
library — not an AI execution backend.

## What It Does

CoreRunner provides two public surfaces:

### 1. `safe_run()` — lightweight subprocess primitive

A standalone function with no RxP dependency, used by all AI execution
backends (TeamExecutor, DAGExecutor, CritiqueExecutor):

```python
from core_runner.process import safe_run

result = safe_run(
    ["claude", "--model", model, "--message", prompt],
    cwd=working_dir,
    timeout_seconds=3600,
)
# result.returncode, result.stdout, result.stderr, result.timed_out
```

Safety guarantees:

- **Process-group leader** — `start_new_session=True` so the child owns its own process group
- **Full-tree kill on timeout** — `os.killpg(SIGKILL)` reaps all descendants (sub-agents, nested tool calls), not just the direct child
- **SIGTERM propagation** — transient handler ensures the child group is killed if the Python supervisor process is itself killed (OOM, supervisor stop)

### 2. `CoreRunner.run(invocation)` — RxP invocation dispatcher

The full runtime dispatch layer used by OperationsCenter's `direct_local` and
`aider_local` adapters. Routes by `runtime_kind` to a registered runner and
returns a normalized RxP `RuntimeResult` with stdout/stderr captured to files
as `ArtifactDescriptor` entries.

| Runner | `runtime_kind` | What it does |
|--------|----------------|--------------|
| `SubprocessRunner` | `subprocess` | Safe subprocess via `safe_run()` + file capture (default) |
| `ManualRunner` | `manual` | Caller-supplied dispatcher callable |
| `HttpRunner` | `http` | Synchronous HTTP request/response |
| `AsyncHttpRunner` | `http_async` | Kickoff POST + poll until terminal status |

## Where It Fits

```
TeamExecutor / DAGExecutor / CritiqueExecutor
    └─ core_runner.safe_run()   ← process-group-safe CLI subprocess

OperationsCenter → DirectLocalBackendAdapter
                     └─ CoreRunner.run(invocation)
                           └─ SubprocessRunner → safe_run() → claude CLI
                                └─ RuntimeResult (with file-captured artifacts)
```

## This Repo Is

- canonical process-group-safe subprocess primitive for all backends
- RxP invocation dispatcher for `direct_local` / `aider_local` OC adapters
- stdout/stderr capture and `ArtifactDescriptor` production (RxP path only)
- `runtime_kind`-based dispatch registry

## This Repo Is Not

- an AI execution backend (that is TeamExecutor, DAGExecutor, CritiqueExecutor)
- an orchestration planner or routing layer
- responsible for agent topology, stage planning, or verification
