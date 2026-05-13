---
architecture_status: CURRENT
canonical: true
supersedes: []
superseded_by: null
---

# Documentation Status

ProtocolWarden documentation uses explicit frontmatter to distinguish current
canonical pages from archival material.

## Status values

- `CURRENT`
- `HISTORICAL`
- `DEPRECATED`
- `MIGRATED`
- `ARCHIVED`

## Current page rules

- Current pages must declare `architecture_status: CURRENT`.
- Current pages must set `canonical: true`.
- Current pages should point `superseded_by` to `null`.

## Historical page rules

- Historical pages must declare a non-current status.
- Historical pages must set `canonical: false`.
- Historical pages should point `superseded_by` at the current canonical page
  when one exists.

## Operational intent

This metadata is for search, review, and site maintenance. It does not change
the RepoGraph enforcement boundary.
