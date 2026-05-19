# Execution Routing

Execution routing is the handoff from planning intent to lane and backend
selection.

## Main path

- OperationsCenter produces or maps a proposal
- SwitchBoard returns a routing decision (CxRP lane decision)
- OperationsCenter binds runtime and capability context
- An owned execution backend performs invocation:
  - **TeamExecutor** — coordinator/worker/verifier pattern for team topology tasks
  - **DAGExecutor** — rustworkx DAG with concurrent layer execution for structured workflows
  - **CritiqueExecutor** — adversarial (proposer+critic) and reflexion modes for quality-gated tasks
  - **ExecutorRuntime** — managed project workflow via RxP for direct-local execution

## Backend selection

The `backend_name` field on the CxRP lane decision identifies which executor
handles the invocation. SwitchBoard selects the backend based on the routing
proposal; OperationsCenter dispatches to the corresponding adapter.
