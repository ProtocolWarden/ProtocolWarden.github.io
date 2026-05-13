# ProtocolWarden

ProtocolWarden.github.io is the canonical public-facing knowledge surface for
the ProtocolWarden ecosystem.

It explains:

- what exists
- why it exists
- how it connects
- what boundaries are enforced
- how contracts interact
- how execution flows
- how governance works
- what is public vs private

## What This Site Is

- the public documentation surface
- the ecosystem entrypoint
- the architecture explanation layer
- the protocol and specification hub
- the ontology and topology explorer
- the governance and public-projection layer

## What This Site Is Not

- a runtime system
- an orchestration layer
- a deployment manager
- a backend service
- an execution environment

## Start Here

- [Getting Started](getting-started/index.md)
- [Ecosystem Overview](overview/ecosystem.md)
- [Layered Architecture](architecture/layered-architecture.md)
- [Protocol Overview](protocols/index.md)
- [Repository Catalog](repos/index.md)

## Operational References

- [RepoGraph Post-PASS Hardening Baseline](architecture/stable-baselines/repograph-post-pass-hardening-v1.md)
- [Semantic Federation](operations/semantic-federation.md)

## Ecosystem in 60 Seconds

ProtocolWarden is a contract-first platform built around explicit boundaries:

- `CxRP` owns cross-repo execution and routing semantics
- `RxP` owns runtime invocation semantics
- `OperationsCenter` owns orchestration and governance behavior
- `SwitchBoard` owns lane and backend selection
- `ExecutorRuntime` owns runtime invocation mechanics
- `RepoGraph` owns the shared ontology, topology, projection, and boundary language
- `PlatformManifest` publishes the public graph instance and public-safe projections
- the private-truth layer supplies private graph truth in that language
- `Custodian` consumes RepoGraph boundary artifacts and enforces public-surface drift checks
- `PlatformDeployment` (deployment overlay repo) owns deployment and local
  hosting concerns

For a short operator model, see
[architecture/simple-platform-model.md](architecture/simple-platform-model.md).

## Initial Homepage Diagram

```mermaid
graph TD
    PKS[Public Knowledge Surface]
    SITE[ProtocolWarden.github.io]
    ONT[Ontology]
    TOP[Topology]
    GOV[Governance]
    PROTO[Protocol Layer\nCxRP / RxP / Contracts]
    CTRL[Control Layer\nOperationsCenter / SwitchBoard]
    RUN[Runtime Layer\nManaged Projects / ExecutorRuntime]

    PKS --> SITE
    SITE --> ONT
    SITE --> TOP
    SITE --> GOV
    ONT --> PROTO
    TOP --> PROTO
    GOV --> CTRL
    PROTO --> CTRL
    CTRL --> RUN
```

## Core Repo Constellation

```mermaid
graph LR
    OC[OperatorConsole]
    OPS[OperationsCenter]
    SB[SwitchBoard]
    CX[CxRP]
    RX[RxP]
    ER[ExecutorRuntime]
    PM[PlatformManifest]
    PT[Private truth layer]
    SR[SourceRegistry]
    WS[PlatformDeployment]
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
    OPS --> PT
    WS --> OPS
    WH -. utility only .-> OPS
```

## Protocol Stack Summary

- **Contracts:** CxRP, RxP
- **Control plane:** OperatorConsole, OperationsCenter, SwitchBoard
- **Runtime layer:** ExecutorRuntime, managed backends, managed projects
- **Inventory and governance:** PlatformManifest, private topology inputs,
  Custodian, SourceRegistry, PlatformDeployment
- **Utility tooling:** Warehouse

## Documentation Philosophy

This repository exists to preserve architectural intent and reduce cognitive
load. The public site should make the ecosystem understandable without forcing
contributors to reverse-engineer the platform from source alone.
