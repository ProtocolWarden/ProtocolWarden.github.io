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

### Control Plane

- OperatorConsole
- OperationsCenter
- SwitchBoard
- CxRP
- RxP
- ExecutorRuntime

### Platform Inventory and Governance

- PlatformManifest
- private topology repositories
- SourceRegistry
- PlatformDeployment
- Custodian
- Warehouse
- ProtocolWarden.github.io

### Managed Projects and Capability Providers

- managed private projects
- SourceFoundry
- backend and tool integrations

## Why the Repo Split Exists

The split is deliberate:

- protocols remain canonical in protocol repos
- orchestration remains canonical in orchestration repos
- runtime mechanics remain canonical in runtime repos
- topology and visibility remain canonical in manifest repos
- public documentation remains canonical in this repo

That separation reduces schema duplication, ownership drift, and god-repo
behavior.
