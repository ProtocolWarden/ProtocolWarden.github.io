# Repo Constellation

Full repo graph showing primary dependencies and data flows.

```mermaid
graph LR
    OC[OperatorConsole]
    OPS[OperationsCenter]
    SB[SwitchBoard]
    CX[CxRP]
    RX[RxP]
    ER[ExecutorRuntime]
    RG[RepoGraph]
    PM[PlatformManifest]
    PT[Private truth layer]
    SR[SourceRegistry]
    PD[PlatformDeployment]
    CU[Custodian]
    WH[Warehouse]

    OC --> OPS
    OPS --> SB
    OPS --> CX
    OPS --> RX
    OPS --> ER
    OPS --> PM
    OPS --> PT
    OPS --> SR
    OPS --> CU
    PM --> RG
    CU --> RG
    PD --> OPS
    WH -. utility only .-> OPS
```

## Notes

- `private-truth layer` is not a browseable public repo; it is named here as a
  boundary participant.
- `WH` (Warehouse) is utility-only — it packages context but does not govern or
  orchestrate.
- `PD` (PlatformDeployment) feeds the control plane at the environment level.
