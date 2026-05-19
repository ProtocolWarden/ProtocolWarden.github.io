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
    SB-->>OPS: lane decision (backend_name, worker_backend)
    OPS->>BE: dispatch to backend adapter
    note over BE: TeamExecutor / DAGExecutor / CritiqueExecutor<br/>— or —<br/>DirectLocal / AiderLocal (via ExecutorRuntime subprocess layer)
    BE->>MP: execute workflow or agent topology
    MP-->>BE: artifacts and reports
    BE-->>OPS: normalized ExecutionResult
    OPS->>CU: validate policy and hygiene boundaries
```

## AI execution backends (ADR 0005)

The three AI execution backends implement distinct multi-agent topologies:

| Backend | Pattern | Primary use |
|---------|---------|-------------|
| TeamExecutor | Coordinator → workers → verifier cycles | Team topology, parallel agent stages |
| DAGExecutor | DAG with concurrent layer execution | Structured multi-step workflows |
| CritiqueExecutor | Adversarial proposer/critic or Reflexion | Quality-gated tasks, adversarial review |

All three call the Claude Code or Codex CLI via subprocess internally
(`worker_backend` from SwitchBoard lane decision).

## Direct-local and aider-local adapters

For simpler single-agent tasks, OperationsCenter uses its `direct_local` and
`aider_local` adapters. These delegate subprocess mechanics to
**ExecutorRuntime** — a library that provides process-group-safe child process
execution, timeout enforcement, and stdout/stderr capture to files.

```
DirectLocalBackendAdapter → ExecutorRuntime.run() → SubprocessRunner → claude CLI
AiderLocalBackendAdapter  → ExecutorRuntime.run() → SubprocessRunner → aider CLI
```

ExecutorRuntime is not an AI execution backend; it is a subprocess mechanics
library shared by those two adapters.

## worker_backend propagation

SwitchBoard encodes the CLI backend preference (`claude_code` or `codex_cli`)
in `LaneDecision.metadata["worker_backend"]`. OperationsCenter forwards this
through the adapter into the executor, where it controls which CLI is spawned.
