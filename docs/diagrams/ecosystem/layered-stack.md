# Ecosystem Layered Stack

```mermaid
graph TD
    DOCS[Documentation]
    GOV[Governance and Inventory]
    PROTO[Protocols]
    CTRL[Control Plane]
    RUN[Runtime and Managed Projects]
    HOST[Deployment]

    DOCS --> GOV
    GOV --> PROTO
    PROTO --> CTRL
    CTRL --> RUN
    HOST --> CTRL
```
