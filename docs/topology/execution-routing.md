# Execution Routing

Execution routing is the handoff from planning intent to lane and backend
selection.

## Main path

- OperationsCenter produces or maps a proposal
- SwitchBoard returns a routing decision
- OperationsCenter binds runtime and capability context
- ExecutorRuntime or adapters perform invocation
