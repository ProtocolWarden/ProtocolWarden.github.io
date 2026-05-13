# RepoGraph Boundary

RepoGraph defines the language. It does not own the private truth that is
expressed in that language.

## Boundary split

| Repo | Responsibility |
| --- | --- |
| RepoGraph | graph vocabulary, schema governance, projection semantics, boundary artifact shape |
| PlatformManifest | public-safe projection publisher |
| private-truth layer | private truth source and boundary artifact generation |
| Custodian | fail-closed verification of boundary artifacts |
| OperationsCenter | consumes graph context, does not own semantics |

## Boundary rule

Automation may materialize the boundary artifact. Enforcement only consumes it.
Custodian must fail closed when the required boundary artifact is absent.

