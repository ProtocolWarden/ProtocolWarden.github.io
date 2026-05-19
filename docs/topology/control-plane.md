# Control Plane

The control plane is the part of the ecosystem that plans, routes, and governs.

## Control-plane repos

- OperatorConsole
- OperationsCenter
- SwitchBoard
- CxRP
- RxP
- ExecutorRuntime *(subprocess mechanics library; not an AI execution backend)*

**ExecutorRuntime** provides process-group-safe subprocess execution, timeout
enforcement, and stdout/stderr capture. It is a library dependency of
OperationsCenter's `direct_local` and `aider_local` adapters — not a
standalone executor or routing participant.

## AI execution backend layer

Owned executors dispatched by OperationsCenter (post ADR 0005):

- TeamExecutor — coordinator/worker/verifier topology for team-shaped tasks
- DAGExecutor — rustworkx DAG with concurrent layer execution
- CritiqueExecutor — adversarial proposer/critic and reflexion quality loops

These are not control-plane components; they receive dispatch and return
normalized results. They depend on CxRP and RxP contracts but do not
participate in routing decisions. They do not use ExecutorRuntime.

## Non-control-plane repos

- PlatformManifest
- private-truth layer
- Custodian
- PlatformDeployment
- Warehouse
- managed project repos

Those support or constrain the control plane but do not replace it.
