# Ecosystem Graph

```mermaid
graph TD
    FRONT[ProtocolWarden/ProtocolWarden]
    OC[OperatorConsole]
    OPS[OperationsCenter]
    SB[SwitchBoard]
    CX[CxRP]
    RX[RxP]
    ER[ExecutorRuntime]
    TE[TeamExecutor]
    DE[DagExecutor]
    CE[CritiqueExecutor]
    RG[RepoGraph]
    PM[PlatformManifest]
    PT[Private truth layer]
    CU[Custodian]
    WS[PlatformDeployment]
    WH[Warehouse]
    SR[SourceRegistry]
    DOCS[ProtocolWarden.github.io]

    FRONT --> DOCS
    DOCS --> PM
    DOCS --> RG
    DOCS --> CX
    DOCS --> RX
    OC --> OPS
    OPS --> SB
    OPS --> CX
    OPS --> RX
    OPS --> ER
    OPS --> TE
    OPS --> DE
    OPS --> CE
    OPS --> PM
    OPS --> PT
    OPS --> SR
    OPS --> CU
    TE --> CX
    TE --> RX
    DE --> CX
    DE --> RX
    CE --> CX
    CE --> RX
    WS --> OPS
    WH --> OPS
```
