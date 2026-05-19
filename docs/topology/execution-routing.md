# Execution Routing

Execution routing is the handoff from planning intent to lane and backend
selection.

## Main path

- OperationsCenter produces or maps a proposal
- SwitchBoard returns a routing decision (`LaneDecision` with `backend_name` and `metadata["worker_backend"]`)
- OperationsCenter dispatches to the corresponding backend adapter

## AI execution backends

The three owned AI execution backends run multi-agent topologies:

- **TeamExecutor** — coordinator/worker/verifier cycle for team topology tasks
- **DAGExecutor** — rustworkx DAG with concurrent layer execution for structured workflows
- **CritiqueExecutor** — adversarial (proposer+critic) and reflexion modes for quality-gated tasks

## Direct-local adapters

For simpler single-agent tasks, OperationsCenter dispatches to:

- **DirectLocal** — spawns claude CLI directly in the managed project workspace
- **AiderLocal** — spawns aider CLI directly in the managed project workspace

Both use **ExecutorRuntime** as their subprocess mechanics substrate (process-group-safe
execution, timeout, stdout/stderr capture). ExecutorRuntime is a library, not a
peer execution backend.

## Backend selection

`LaneDecision.backend_name` identifies which adapter handles the invocation.
`LaneDecision.metadata["worker_backend"]` encodes the CLI preference
(`claude_code` or `codex_cli`) for backends that support both.
SwitchBoard sets both; OperationsCenter reads both at dispatch time.
