# Control Plane

The control plane is the part of the ecosystem that plans, routes, and governs.

## Control-plane repos

- OperatorConsole
- OperationsCenter
- SwitchBoard
- CxRP
- RxP
- ExecutorRuntime

## Execution backend layer

Owned executors dispatched by OperationsCenter (post ADR 0005):

- TeamExecutor
- DagExecutor
- CritiqueExecutor

These are not control-plane components; they receive dispatch and return
normalized results. They depend on CxRP and RxP contracts but do not
participate in routing decisions.

## Non-control-plane repos

- PlatformManifest
- private-truth layer
- Custodian
- PlatformDeployment
- Warehouse
- managed project repos

Those support or constrain the control plane, but they do not replace it.
