# ExecutorRuntime

## Mission

Subprocess execution mechanics for RxP-shaped invocations. A Python library,
not an AI execution backend.

## What It Does

ExecutorRuntime is the subprocess substrate used by OperationsCenter's
`direct_local` and `aider_local` backend adapters. It wraps the mechanics of
running a child process safely and capturing its output:

- **Process-group safety** — spawns the child as a new session leader
  (`start_new_session=True`); on timeout kills the entire process group
  (`os.killpg(SIGKILL)`) to reap any descendants the child may have spawned.
- **Timeout enforcement** — configurable per-invocation timeout.
- **Output capture** — stdout and stderr written to files inside a capture
  directory; paths returned as `ArtifactDescriptor` entries in `RuntimeResult`.
- **Environment overlay** — per-invocation env var overrides.
- **Exit-code normalization** — maps exit codes and signals to `RuntimeResult.status`.
- **Dispatch by `runtime_kind`** — registry of runners:

| Runner | `runtime_kind` | What it does |
|--------|----------------|--------------|
| `SubprocessRunner` | `subprocess` | Local subprocess with process-group safety (default) |
| `ManualRunner` | `manual` | Caller-supplied dispatcher callable |
| `HttpRunner` | `http` | Synchronous HTTP request/response |
| `AsyncHttpRunner` | `http_async` | Kickoff POST + poll until terminal status |

## Where It Fits

ExecutorRuntime is a **library dependency** of OperationsCenter, not a
standalone execution backend. The call chain for `direct_local` and
`aider_local` executions is:

```
OperationsCenter → DirectLocalBackendAdapter
                     └─ ExecutorRuntime.run(invocation)
                           └─ SubprocessRunner → child process (claude CLI)
                                └─ RuntimeResult → ExecutionResult
```

The three **AI execution backends** (TeamExecutor, DAGExecutor,
CritiqueExecutor) are distinct from ExecutorRuntime. They have their own
coordinator/worker/verifier or DAG architectures and call the Claude or Codex
CLI directly via subprocess — they do not use ExecutorRuntime.

## This Repo Is

- subprocess execution substrate for `direct_local` / `aider_local` OC adapters
- process-group-safe child process lifecycle management
- stdout/stderr capture and artifact descriptor production
- `runtime_kind`-based dispatch registry

## This Repo Is Not

- an AI execution backend (that is TeamExecutor, DAGExecutor, CritiqueExecutor)
- an orchestration planner or routing layer
- used by TeamExecutor, DAGExecutor, or CritiqueExecutor
