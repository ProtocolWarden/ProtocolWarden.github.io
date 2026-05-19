# Execution Flow

```mermaid
sequenceDiagram
    participant OC as OperatorConsole
    participant OPS as OperationsCenter
    participant PM as PlatformManifest
    participant SB as SwitchBoard
    participant BE as ExecutionBackend
    participant MP as ManagedProject
    participant CU as Custodian

    OC->>OPS: task intent
    OPS->>PM: resolve topology and visibility
    OPS->>SB: route proposal using CxRP
    SB-->>OPS: lane decision (backend_name)
    OPS->>BE: dispatch using RxP
    note over BE: TeamExecutor / DAGExecutor / CritiqueExecutor / ExecutorRuntime
    BE->>MP: execute workflow or agent topology
    MP-->>BE: artifacts and reports
    BE-->>OPS: normalized runtime result
    OPS->>CU: validate policy and hygiene boundaries
```

## Execution backends (ADR 0005)

| Backend | Pattern | Primary use |
|---------|---------|-------------|
| TeamExecutor | Coordinator → workers → verifier | Team topology, parallel agent tasks |
| DAGExecutor | DAG with concurrent layer execution | Structured multi-step workflows |
| CritiqueExecutor | Adversarial proposer/critic or Reflexion | Quality-gated tasks, adversarial review |
| ExecutorRuntime | Managed project via RxP | Direct-local execution, single-agent tasks |
