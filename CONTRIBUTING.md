# Contributing to ProtocolWarden.github.io

This repository hosts the public documentation surface for the ProtocolWarden
ecosystem. Changes here affect architecture notes, repo roles, public doctrine,
and the site structure rendered by MkDocs.

## Before You Start

- Check open issues before proposing a docs change
- For architecture updates, link the repo or decision record the change reflects
- Keep public docs aligned with the current RepoGraph / manifest ownership model

## Local Development

```bash
python -m pip install -r requirements.txt
mkdocs serve
```

## Contribution Guidelines

- Keep pages public-safe
- Prefer concise, explicit architecture language
- Do not copy private graph data, private paths, or private endpoints into the site
- Update navigation when adding or moving pages

## Pull Requests

- Keep PRs focused on one documentation concern
- Include screenshot or preview notes for visible layout changes
- Update the relevant index pages when adding new docs

## Code of Conduct

This project follows the [Contributor Covenant v2.1](CODE_OF_CONDUCT.md).
