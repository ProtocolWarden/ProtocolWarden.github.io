---
architecture_status: CURRENT
canonical: true
supersedes: []
superseded_by: null
---

# Simple Platform Model

RepoGraph defines the language.
private-truth layer stores private truth.
PlatformManifest publishes safe public views.
Custodian verifies boundaries.
OperationsCenter orchestrates.
PlatformDeployment deploys.
Warehouse packages context.
ProtocolWarden/ProtocolWarden is the short public front door.
ProtocolWarden.github.io is the full public knowledge surface.

## Flow

```mermaid
graph LR
    RG[RepoGraph] --> PM[PlatformManifest]
    RG --> PRM[private-truth layer]
    PRM --> CUST[Custodian]
    PM --> OC[OperationsCenter]
    PD[PlatformDeployment] --> OC
    WH[Warehouse] -. context only .-> OC
```

## Boundary artifact flow

```mermaid
graph LR
    PRM[private-truth layer] --> ART[Boundary artifact file]
    ART --> CUST[Custodian]
    CUST --> REP[Verification report]
```

## Projection profile flow

```mermaid
graph LR
    PRM[private-truth layer graph truth] --> RG[RepoGraph projection profile]
    RG --> PUB[Public-safe projection]
    RG --> AUD[Audit/internal projection]
```

The simple model is descriptive only. The RepoGraph schema, projection, and
boundary rules still enforce the actual boundaries.
