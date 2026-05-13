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
    PT[Private truth layer]
    CU[Custodian]
    WS[PlatformDeployment]
    WH[Warehouse]
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
    OPS --> PT
    OPS --> SR
    OPS --> CU
    WS --> OPS
    WH --> OPS
```
