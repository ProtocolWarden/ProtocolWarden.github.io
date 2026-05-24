# Protocol Stack

```mermaid
graph TD
    subgraph contracts ["Contract / Protocol Layer"]
        CX["CxRP<br/>cross-repo execution routing"]
        RX["RxP<br/>runtime invocation"]
    end
    subgraph graph ["Semantic Graph Layer"]
        RG["RepoGraph<br/>graph semantics and schema"]
        PM["PlatformManifest<br/>public-safe projection"]
    end
    subgraph control ["Control Layer"]
        OPS[OperationsCenter]
        SB[SwitchBoard]
    end
    subgraph runtime ["Runtime Layer"]
        ER["CoreRunner<br/>subprocess mechanics library"]
        BE["TeamExecutor / DAGExecutor / CritiqueExecutor<br/>AI execution backends"]
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
