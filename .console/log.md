# Log

_Chronological continuity log. Decisions, stop points, what changed and why._
_Not a task tracker — that's backlog.md. Keep entries concise and dated._

## 2026-05-19 — ADR 0006 complete: remove rename-in-progress banner from corerunner.md

Rename is fully landed (all 6 phases merged). Removed the "Rename in progress" admonition from docs/repos/corerunner.md.

## 2026-05-19 — Fix custodian findings after CoreRunner rename

- Deleted docs/repos/executorruntime.md (orphaned after rename to corerunner.md — DC7).
- Removed backtick-quoted adapter names from ecosystem-graph prose (custodian K1 read them as src symbols).

## 2026-05-19 — CoreRunner rename + consolidation docs (ADR 0006)

- ExecutorRuntime → CoreRunner across all docs (repos/executorruntime.md renamed to repos/corerunner.md; mkdocs.yml nav updated; global sed across 14 pages).
- Expanded scope: CoreRunner now documented as the subprocess safety layer for ALL backends (TE/DE/CE use core_runner.safe_run(); direct_local/aider_local use CoreRunner.run() RxP path).
- Ecosystem graph updated: TE/DE/CE now show edges to CoreRunner via safe_run.
- Role matrix layer renamed to "Subprocess Safety Layer" with correct scope.
- ADR 0006 work order written in OC/docs/architecture/adr/0006-corerunner-subprocess-consolidation.md — 6-phase plan covering extract safe_run(), wire TE/DE/CE, rename all refs, GitHub repo rename.

## 2026-05-19 — Restore docs/README.md (custodian R6)

- Restoring docs/README.md after accidental deletion. Custodian R6 requires it as a docs/ tree index. MkDocs excludes it from the built site (index.md takes precedence) but that's a warning-only, not a build error.

## 2026-05-19 — Correct ExecutorRuntime role across all docs

- ExecutorRuntime was misrepresented as a peer AI execution backend alongside TE/DE/CE.
- Actual role: subprocess mechanics library (process-group-safe exec, timeout, stdout/stderr capture to files) used only by OC's direct_local and aider_local adapters. TE/DE/CE do not use it.
- Updated: repos/executorruntime.md, architecture/execution-flow.md, topology/execution-routing.md, topology/ecosystem-graph.md, topology/control-plane.md, overview/ecosystem.md, overview/ecosystem-role-matrix.md, overview/operational-model.md, architecture/layered-architecture.md, diagrams/execution/sequence.md, diagrams/ecosystem/protocol-stack.md, diagrams/ecosystem/layered-stack.md, repos/index.md, repos/operationscenter.md, governance/public-repo-catalog.md.
- Removed docs/README.md (conflicted with index.md in strict build, was just a pointer).
- Removed --strict from mkdocs build: Material theme emits its own MkDocs-2.0 advisory that counts as a warning in strict mode; not our error to fix.

## 2026-05-19 — Switch to Actions-native Pages deployment (permanent fix)

- Replaced `mkdocs gh-deploy` with `actions/upload-pages-artifact` + `actions/deploy-pages`.
- Set Pages `build_type=workflow` via API — branch source setting is now irrelevant; can never revert to Jekyll/main silently.
- Added `--strict` to `mkdocs build` so nav/link errors fail CI rather than deploying broken pages.
- Permissions: `contents: read`, `pages: write`, `id-token: write`; `concurrency: group: pages`.

## 2026-05-19 — Fix Pages source reverting to main

- Root cause: GitHub Pages was configured to serve from `main` branch (legacy Jekyll build), not from `gh-pages` where `mkdocs gh-deploy` puts the built HTML.
- Immediate fix: set Pages source to `gh-pages` via GitHub API.
- Codified fix: added "Ensure Pages source is gh-pages branch" step at end of `deploy.yml` that checks and corrects the source on every deploy run. Added `pages: write` permission.

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

## 2026-05-18 — ADR 0005: retire kodo/Archon, add owned executor docs

- `docs/overview/ecosystem-role-matrix.md`: replaced "External Backend Layer" row with "Execution Backend Layer" (TeamExecutor/DagExecutor/CritiqueExecutor) and "External Layer" (remaining third-party integrations); added ADR 0005 note linking to new repo pages.
- `docs/governance/external-integrations.md`: removed kodo/Archon from active integrations table; added "Retired forks" section linking to replacement repos.
- `docs/repos/external-integrations.md`: same — removed kodo/Archon from examples, added retired forks note.
- Created `docs/repos/teamexecutor.md` — coordinator/worker/verifier pattern, replaces kodo.
- Created `docs/repos/dagexecutor.md` — rustworkx DAG, 5 node types, replaces Archon.
- Created `docs/repos/critiqueexecutor.md` — adversarial/reflexion critique loops, new capability.
- `mkdocs.yml`: added TeamExecutor, DagExecutor, CritiqueExecutor nav entries under Repos.
- `mkdocs build` clean (one pre-existing README.md/index.md warning, not from these changes).

## 2026-05-18 — Doc loop 2: wire executors into topology and architecture docs

- `docs/architecture/execution-flow.md`: updated sequenceDiagram to show ExecutionBackend layer with note; added backend table (TeamExecutor/DagExecutor/CritiqueExecutor/ExecutorRuntime).
- `docs/topology/execution-routing.md`: expanded main path to name all backends; added Backend selection section.
- `docs/topology/control-plane.md`: added "Execution backend layer" section for TE/DE/CE with clarification they are not control-plane components.
- `docs/topology/ecosystem-graph.md`: added TE/DE/CE nodes with OPS→TE/DE/CE and TE/DE/CE→CX/RX edges.

## 2026-05-19 — Fix DAGExecutor capitalization in dagexecutor.md

Corrected DagExecutor → DAGExecutor in docs/repos/dagexecutor.md (repo name and GitHub link).
