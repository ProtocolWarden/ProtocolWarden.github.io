# Manifest Projection

```mermaid
graph TD
    Private[Private Topology Layer\nprivate superset]
    Rules[Projection Rules]
    Public[PlatformManifest\npublic-safe projection]
    Local[Local Manifest\nruntime-only overlay]
    Custodian[Custodian]

    Private --> Rules
    Rules --> Public
    Local -. never published .-> Public
    Public --> Custodian
```
