# Public / Private Projection Flow

Shows how private truth becomes a public-safe projection and how enforcement consumes it.

```mermaid
graph TD
    PT[Private truth layer\nprivate graph truth]
    RG[RepoGraph\ngraph schema and semantics]
    RULES[Projection rules\nvisibility and redaction]
    PM[PlatformManifest\npublic-safe projection]
    BA[Boundary artifact\nfrozen export]
    CU[Custodian\nfail-closed verifier]
    OPS[OperationsCenter]
    OC[OperatorConsole]
    SB[SwitchBoard]

    PT -->|private truth export| RULES
    RG -->|schema and semantics| RULES
    RULES --> PM
    PM --> BA
    BA --> CU
    CU -->|verified context| OPS
    CU -->|verified context| OC
    CU -->|verified context| SB
```

## Rules

- Private truth never flows directly to consumers — it passes through projection
  and redaction first.
- `PlatformManifest` owns the public-safe projection surface; it does not own
  private truth.
- `Custodian` fails closed when the boundary artifact is absent.
- Consumers (`OperationsCenter`, `OperatorConsole`, `SwitchBoard`) receive
  verified public-safe context only.
- Local manifests used at runtime are never published to the public surface.
