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
    RG[RepoGraph]
    PM[PlatformManifest]
    PT[Private truth layer]
    CU[Custodian]
    WS[PlatformDeployment]
    WH[Warehouse]
    SR[SourceRegistry]
    VF[VideoFoundry]
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
    OPS --> PM
    OPS --> PT
    OPS --> SR
    OPS --> CU
    OPS --> VF
    WS --> OPS
    WH --> OPS
```
