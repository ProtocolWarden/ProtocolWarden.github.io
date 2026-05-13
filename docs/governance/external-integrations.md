# External Integrations

External integrations are not automatically core ProtocolWarden repos.
They become platform components only when an adapter, contract, and boundary
story exists for them.

## Current examples

| Repo | Role | Notes |
| --- | --- | --- |
| Archon | external integration | candidate capability source |
| firecrawl | external integration | candidate backend / crawl integration |
| kodo | external integration | candidate backend or forked dependency |
| PraisonAI | external integration | candidate backend or orchestration input |
| Wan2GP | external integration | candidate capability source |
| openclaw | external integration | candidate integration surface |
| Zonos-API | external integration | candidate backend API |
| neuro-game-sdk | external integration | candidate capability source |

## Rules

- Forks are not core architecture by default.
- External repos are documented as dependencies, adapters, or capability
  sources.
- A repo only becomes part of the platform when its contracts and boundaries
  are explicit.
- `SourceRegistry` tracks source and fork lifecycle.

## Related pages

- [Public Repository Catalog](public-repo-catalog.md)
- [Profile README vs Pages Site](profile-readme-vs-pages-site.md)
- [SourceRegistry](../repos/sourceregistry.md)
