# Ecosystem Map

```mermaid
graph TD
    DOCS[ProtocolWarden.github.io]
    PM[PlatformManifest]
    PRM[Private Topology\nRepository]
    OC[OperatorConsole]
    OPS[OperationsCenter]
    SB[SwitchBoard]
    CX[CxRP]
    RX[RxP]
    ER[ExecutorRuntime]
    CU[Custodian]
    WS[PlatformDeployment]
    SR[SourceRegistry]
    WH[Warehouse]
    MP[Managed Private\nProject]

    DOCS --> PM
    DOCS --> CX
    DOCS --> RX
    DOCS --> OPS
    PM --> PRM
    OC --> OPS
    OPS --> SB
    OPS --> ER
    OPS --> CU
    OPS --> MP
    OPS --> SR
    OPS --> WH
    OPS --> PM
    OPS --> CX
    OPS --> RX
    WS --> OPS
```
