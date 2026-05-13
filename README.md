# ProtocolWarden.github.io

Canonical public-facing documentation surface for the ProtocolWarden ecosystem.

Published site: <https://protocolwarden.github.io/>

## What This Repo Is

- the GitHub Pages documentation repository for the ProtocolWarden ecosystem
- the public knowledge layer: architecture, protocols, ontology, topology, governance
- the canonical reference for what is public, what is private, and why
- a current-only public-safe projection — no archival or private topology

## What This Repo Is Not

- a runtime system, orchestrator, or execution environment
- a deployment stack or backend service
- a source of private truth or restricted operational material

## Getting Started

Visit <https://protocolwarden.github.io/> to browse the site.

For local development:

```bash
pip install mkdocs-material
mkdocs serve
```

The GitHub profile README (short front door) lives in the separate
[`ProtocolWarden`](https://github.com/ProtocolWarden/ProtocolWarden) repository.

## Architecture Overview

The site is built with MkDocs + Material for MkDocs. Content lives in `docs/`.
Navigation is declared in `mkdocs.yml`. The deploy workflow (`.github/workflows/deploy.yml`)
runs `mkdocs gh-deploy` on every push to `main`, publishing to the `gh-pages` branch.

```
docs/               # all documentation source
mkdocs.yml          # site configuration and navigation
requirements.txt    # Python dependencies
.github/workflows/  # deploy workflow
```

## Scope

The site is intentionally public-safe. Private topology, internal overlays, and
restricted operational material belong in the relevant private repositories and
must not be copied here directly.
