# Ecosystem Map

```mermaid
graph TD
    FRONT[ProtocolWarden/ProtocolWarden]
    DOCS[ProtocolWarden.github.io]
    RG[RepoGraph]
    PM[PlatformManifest]
    PT[Private truth layer]
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
    VF[VideoFoundry]

    FRONT --> DOCS
    DOCS --> PM
    DOCS --> RG
    DOCS --> CX
    DOCS --> RX
    DOCS --> OPS
    PM --> PT
    OC --> OPS
    OPS --> SB
    OPS --> ER
    OPS --> CU
    OPS --> PT
    OPS --> SR
    OPS --> WH
    OPS --> PM
    OPS --> CX
    OPS --> RX
    OPS --> VF
    WS --> OPS
```
