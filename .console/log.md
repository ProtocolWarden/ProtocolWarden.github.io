# Log

_Chronological continuity log. Decisions, stop points, what changed and why._
_Not a task tracker — that's backlog.md. Keep entries concise and dated._

## 2026-05-13 — Enable navigation.tabs for visible section navigation

- Added `navigation.tabs` and `navigation.tabs.sticky` — puts top-level sections in a persistent tab bar; without this all nav was hidden in the sidebar only.
- Added `navigation.path` (breadcrumbs) and `navigation.indexes` (section index pages clickable).
- Removed `navigation.expand` — with this many sections it made the sidebar a wall of text.
- Removed custodian-audit.yml — this is a markdown-only docs repo, nothing to audit.

## 2026-05-13 — Add GitHub Actions deploy workflow

- Added `.github/workflows/deploy.yml` — runs `mkdocs gh-deploy --force` on push to main.
- Without this the site was serving raw files from the repo root, not the rendered MkDocs Material build.

## 2026-05-13 — Add RepoGraph to Core Repo Constellation diagram

- Added `RG[RepoGraph]` node to the homepage Mermaid diagram with edges `PM --> RG` and `CU --> RG`.
- Renamed `WS[PlatformDeployment]` node identifier to `PD` (legacy `WS` was a WorkStation holdover).
- Added `PD --> OPS` edge to replace the old `WS --> OPS`.

## 2026-05-13 — Public Surface Consolidation Plan workstreams C, D, J

- Homepage (C): rewrote opening to be ecosystem-first; added GitHub org link; explicit profile README vs Pages distinction; replaced abstract diagram with layered subgraph using actual repo names.
- Public repo catalog (D): added `profile_front_door` row (ProtocolWarden/ProtocolWarden) and `knowledge_surface` row (ProtocolWarden.github.io).
- Diagrams (J): layered stack updated with current repo names; added repo-constellation, protocol-stack, projection-flow pages; updated diagrams index and mkdocs.yml nav.
- Workstreams E, H, I, K, L verified already complete from prior sessions.

## Stop Points

_Where did you leave off? What should be verified next session?_

- Consolidation plan complete. Verify site renders correctly after deploy workflow runs.

## Notes

_Free-form scratch. Clear periodically — old entries can be deleted once no longer relevant._

---

## 2026-05-13 — Expand architectural-invariants.md with per-repo table and ARCH detector list

- Added per-repo invariant table (What must always be / must never become) covering RepoGraph, PlatformManifest, PlatformDeployment, Warehouse, PrivateManifest, Custodian, OperationsCenter.
- Added ARCH detector table (ARCH1-ARCH4) documenting what each machine-checks.
- Added X2 cross-repo import enforcement section.

## 2026-05-13 — Add graph-layer-stack diagram

- Added docs/diagrams/ecosystem/graph-layer-stack.md — language → instance → deployment → validation layers.
- Wired into mkdocs.yml nav and diagrams/index.md.
- Explicitly captures the topography boundary: RepoGraph owns vocabulary, PlatformDeployment owns runtime placement truth.

## 2026-05-13 — Custodian phase 2 — README, CHANGELOG, DC7, R6 fixes

- README restructured with What this repo is/is not, Getting Started, Architecture sections.
- CHANGELOG.md added.
- docs/README.md added (R6 fix).
- architecture/index.md and audits/index.md updated with full cross-links.
- protocols/index.md updated with markdown links.
- .custodian/config.yaml: doc_conventions.exclude_path_patterns added for all section index pages (correct top-level placement, not inside audit:).
- pre-commit hook added (.hooks/pre-commit).

## 2026-05-13 — Add CLAUDE.md and .custodian/tmp*.yaml to .gitignore

- Added CLAUDE.md to .gitignore
- Added .custodian/tmp*.yaml to exclude custodian audit temp files
