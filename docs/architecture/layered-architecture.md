# Layered Architecture

The ecosystem is easiest to understand as layered responsibilities.

```mermaid
graph TD
    DOCS["Public Documentation Layer<br/>ProtocolWarden.github.io"]
    GOV["Governance and Inventory Layer<br/>PlatformManifest / private topology repos / Custodian / SourceRegistry"]
    PROTO["Protocol Layer<br/>CxRP / RxP"]
    CTRL["Control Plane<br/>OperatorConsole / OperationsCenter / SwitchBoard"]
    RUN["Runtime and Managed Projects<br/>TeamExecutor / DAGExecutor / CritiqueExecutor / DirectLocal+AiderLocal (via CoreRunner)"]
    HOST["Deployment and Hosting<br/>PlatformDeployment"]

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
