# Log

_Chronological continuity log. Decisions, stop points, what changed and why._
_Not a task tracker — that's backlog.md. Keep entries concise and dated._

## 2026-05-13 — Add GitHub Actions deploy workflow

- Added `.github/workflows/deploy.yml` — runs `mkdocs gh-deploy --force` on push to main.
- Without this the site was serving raw files from the repo root, not the rendered MkDocs Material build.

## 2026-05-13 — Add RepoGraph to Core Repo Constellation diagram

- Added `RG[RepoGraph]` node to the homepage Mermaid diagram with edges `PM --> RG` and `CU --> RG`.
- Renamed `WS[PlatformDeployment]` node identifier to `PD` (legacy `WS` was a WorkStation holdover).
- Added `PD --> OPS` edge to replace the old `WS --> OPS`.

## Recent Decisions

_Log significant choices here so they survive context resets._

| Decision | Rationale | Date |
|----------|-----------|------|
| [what was decided] | [why] | [date] |

## Stop Points

_Where did you leave off? What should be verified next session?_

- [what to pick up next]

## Notes

_Free-form scratch. Clear periodically — old entries can be deleted once no longer relevant._

---
