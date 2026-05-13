# Ecosystem

ProtocolWarden is a multi-repository ecosystem organized around explicit
contracts, visible ownership boundaries, and public/private documentation
projection.

## Core Mission

The ecosystem is designed to coordinate:

- planning
- routing
- execution
- runtime invocation
- artifact production
- policy enforcement
- topology management
- public-safe documentation

without collapsing all semantics into one repository.

## Main Layers

### Public Surface

- [ProtocolWarden/ProtocolWarden](https://github.com/ProtocolWarden/ProtocolWarden)
- [ProtocolWarden.github.io](https://protocolwarden.github.io/)

### Semantic Core

- RepoGraph
- PlatformManifest
- CxRP
- RxP

### Control Plane

- OperatorConsole
- OperationsCenter
- SwitchBoard
- ExecutorRuntime
- VideoFoundry

### Platform Inventory and Governance

- Custodian
- SourceRegistry
- PlatformDeployment
- Warehouse

### Private Truth Boundary

- private-truth layer
- PrivateManifest

### Managed Projects and Capability Providers

- managed private projects
- backend and tool integrations
- external integrations and forked dependencies

## Why the Repo Split Exists

The split is deliberate:

- protocols remain canonical in protocol repos
- orchestration remains canonical in orchestration repos
- runtime mechanics remain canonical in runtime repos
- topology and visibility remain canonical in manifest repos
- public documentation remains canonical in this repo
- managed projects remain consumers of the published ecosystem, not owners of it
- RepoGraph remains the shared semantic substrate

That separation reduces schema duplication, ownership drift, and god-repo
behavior.
