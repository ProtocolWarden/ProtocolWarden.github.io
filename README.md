# ProtocolWarden.github.io

Canonical public-facing documentation surface for the ProtocolWarden ecosystem.

Published site: <https://protocolwarden.github.io/>

This repository is the public knowledge layer for:

- ecosystem overview
- architecture explanation
- protocol and contract documentation
- ontology and topology guidance
- governance and boundary doctrine
- public-safe documentation projections

It is not a runtime, orchestrator, deployment stack, or execution environment.

This repository is the GitHub Pages site for the ProtocolWarden ecosystem. The
GitHub profile README lives in the separate repository
[`ProtocolWarden`](https://github.com/ProtocolWarden/ProtocolWarden), which is
the short public front door on `github.com/ProtocolWarden`.

The site is intentionally current-only. It presents the active public projection
surface and does not keep archival repo pages or historical catalog entries.

For a short operator-facing summary, see
[docs/architecture/simple-platform-model.md](docs/architecture/simple-platform-model.md).

## Stack

- MkDocs
- Material for MkDocs
- Markdown-first documentation
- Mermaid diagrams

## Local development

```bash
pip install mkdocs-material
mkdocs serve
```

## Site identity

- `ProtocolWarden.github.io`: the published documentation website
- `ProtocolWarden`: the GitHub profile README repository
- `ProtocolWarden/ProtocolWarden.github.io`: the repository you are reading now

## Scope

The site is intentionally public-safe. Private topology, internal overlays, and
restricted operational material belong in the relevant private repositories and
must not be copied here directly.
