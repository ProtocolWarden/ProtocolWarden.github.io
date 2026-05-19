# Execution Sequence

```mermaid
sequenceDiagram
    participant Human
    participant Console as OperatorConsole
    participant OC as OperationsCenter
    participant SB as SwitchBoard
    participant BE as Backend Adapter
    participant Managed as Managed Project

    Human->>Console: request work
    Console->>OC: forward intent
    OC->>SB: route using CxRP
    SB-->>OC: LaneDecision (backend_name, worker_backend)
    OC->>BE: dispatch to adapter
    note over BE: TeamExecutor / DAGExecutor / CritiqueExecutor<br/>(multi-agent topologies)<br/>— or —<br/>DirectLocal / AiderLocal<br/>(single-agent via CoreRunner subprocess layer)
    BE->>Managed: execute workflow or agent task
    Managed-->>BE: artifacts
    BE-->>OC: ExecutionResult
```

## Notes

- **TeamExecutor / DAGExecutor / CritiqueExecutor** implement their own coordinator/worker/verifier
  or DAG topologies and call the Claude Code or Codex CLI directly via subprocess.
- **DirectLocal / AiderLocal** are simpler single-agent adapters that use **CoreRunner**
  as a subprocess mechanics library (process-group safety, timeout, stdout/stderr capture).
- CoreRunner is a library dependency of the DirectLocal/AiderLocal adapters,
  not a standalone actor in this sequence.
