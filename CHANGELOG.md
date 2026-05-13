# Changelog

All notable changes to the ProtocolWarden documentation site.

## [Unreleased]

### Added
- GitHub Actions deploy workflow — `mkdocs gh-deploy` on push to `main`.
- Navigation tabs (`navigation.tabs`, `navigation.tabs.sticky`) for top-level section visibility.
- Repo constellation, protocol stack, and projection flow diagram pages.
- Pre-commit hook for log.md enforcement.

### Changed
- Homepage rewritten with ecosystem-first opening and layered architecture diagram.
- Diagrams updated to use current repo names with subgraph layers.
- Public repo catalog: added `profile_front_door` and `knowledge_surface` entries.

### Removed
- `custodian-audit.yml` workflow (docs-only repo, nothing to audit).
- `navigation.expand` (too noisy with many sections).
