# Graph Layer Stack

How the platform builds a complete picture of itself — from shared vocabulary to
public projection to local deployment truth.

```mermaid
graph TB
  subgraph lang["Language Layer — RepoGraph"]
    direction TB
    ONT["ontology<br/>identity · visibility · disclosure modes · planes"]
    TOP["topology<br/>edge kinds · validation · relationship models"]
    PROJ["projection<br/>redaction rules · public-safe surface semantics"]
    SCH["schema<br/>boundary artifact shape · version gates"]
  end

  subgraph pub["Public Instance Layer — PlatformManifest"]
    direction TB
    DECL["declared graph<br/>canonical repo names · edges · visibility"]
    ART["boundary artifact<br/>public-safe projection of the graph"]
  end

  subgraph priv["Private / Runtime Layer"]
    direction TB
    PM_PRIV["PrivateManifest<br/>private names · restricted edges"]
    PD["PlatformDeployment<br/>local topography · runtime placement truth"]
  end

  subgraph val["Validation Layer — Custodian"]
    direction TB
    CU["audit engine<br/>validates public surfaces against boundary artifacts"]
  end

  lang --> pub
  lang --> priv
  pub --> val
  priv --> val
```

## Layer Responsibilities

| Layer | Repo | Owns | Does Not Own |
|-------|------|------|--------------|
| Language | RepoGraph | graph vocabulary — ontology, topology, projection semantics, artifact schemas | graph instances, runtime placement truth |
| Public Instance | PlatformManifest | canonical public graph declaration, boundary artifact publication | graph language definitions, deployment truth |
| Private/Runtime | PrivateManifest, PlatformDeployment | private name overlays, local runtime topography | public projection rules, graph language |
| Validation | Custodian | auditing public repos against boundary artifacts | graph authoring, publication |

## The Topography Boundary

RepoGraph owns the **vocabulary** for topography — what a plane, edge kind, or
deployment node *means*. It does not own runtime placement truth.

Actual deployment truth — which service runs where, which node is provisioned —
lives in PlatformDeployment and local manifests. RepoGraph gives them the
language to express that truth consistently.
