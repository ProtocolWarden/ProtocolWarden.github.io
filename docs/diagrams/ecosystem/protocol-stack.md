# Protocol Stack

```mermaid
graph TD
    subgraph contracts ["Contract / Protocol Layer"]
        CX[CxRP\ncross-repo execution routing]
        RX[RxP\nruntime invocation]
    end
    subgraph graph ["Semantic Graph Layer"]
        RG[RepoGraph\ngraph semantics and schema]
        PM[PlatformManifest\npublic-safe projection]
    end
    subgraph control ["Control Layer"]
        OPS[OperationsCenter]
        SB[SwitchBoard]
    end
    subgraph runtime ["Runtime Layer"]
        ER[ExecutorRuntime]
        BE[backend consumers]
    end

    graph --> contracts
    contracts --> control
    control --> runtime
```

## Protocol ownership

| Protocol | Repo | Owns |
| --- | --- | --- |
| CxRP | CxRP | cross-repo execution routing semantics and contract vocabulary |
| RxP | RxP | normalized runtime invocation and result semantics |
| Graph semantics | RepoGraph | shared repo identity, visibility, topology, and boundary schema |
| Public projection | PlatformManifest | public-safe graph surface and boundary artifact publication |
