# Ecosystem Graph

```mermaid
graph TD
    OC[OperatorConsole]
    OPS[OperationsCenter]
    SB[SwitchBoard]
    CX[CxRP]
    RX[RxP]
    ER[ExecutorRuntime]
    PM[PlatformManifest]
    PRM[Private Topology\nRepository]
    CU[Custodian]
    WS[PlatformDeployment]
    WH[Warehouse]
    MP[Managed Private\nProject]
    SR[SourceRegistry]
    DOCS[ProtocolWarden.github.io]

    DOCS --> PM
    DOCS --> CX
    DOCS --> RX
    OC --> OPS
    OPS --> SB
    OPS --> CX
    OPS --> RX
    OPS --> ER
    OPS --> PM
    OPS --> PRM
    OPS --> SR
    OPS --> CU
    OPS --> MP
    WS --> OPS
    WH --> OPS
```
