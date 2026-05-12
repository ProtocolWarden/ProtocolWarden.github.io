# Layered Architecture

The ecosystem is easiest to understand as layered responsibilities.

```mermaid
graph TD
    DOCS[Public Documentation Layer\nProtocolWarden.github.io]
    GOV[Governance and Inventory Layer\nPlatformManifest / private topology repos / Custodian / SourceRegistry]
    PROTO[Protocol Layer\nCxRP / RxP]
    CTRL[Control Plane\nOperatorConsole / OperationsCenter / SwitchBoard]
    RUN[Runtime and Managed Projects\nExecutorRuntime / managed projects / backends]
    HOST[Deployment and Hosting\nPlatformDeployment]

    DOCS --> GOV
    GOV --> PROTO
    PROTO --> CTRL
    CTRL --> RUN
    HOST --> CTRL
    HOST --> RUN
```

## Interpretation

- documentation explains the ecosystem
- governance and inventory describe and constrain it
- protocol repos define canonical semantics
- control-plane repos make decisions
- runtime systems execute work
- hosting systems run the local environment
