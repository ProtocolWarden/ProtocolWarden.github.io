# Slice 01 - Canonical Docs Consolidation

## Purpose

Replace first-pass ecosystem prose with extracted, normalized, and public-safe
canonical material from the live ProtocolWarden repositories.

This slice is the transition from:

- initial site scaffold
- first-pass repo summaries
- broad architecture framing

to:

- repo-derived canonical docs
- protocol-derived object pages
- generated public-safe indexes
- publishable public ecosystem documentation

## Scope

1. replace broad first-pass prose with canonical material extracted from source repos
2. add generated schema and enum documentation pages
3. wire GitHub Pages or equivalent CI publication workflow
4. add repo-specific diagrams and source-linked cross references

## Inputs

Expected source repos for extraction:

- `OperationsCenter`
- `CxRP`
- `RxP`
- `PlatformManifest`
- private topology repositories
- `Custodian`
- `ExecutorRuntime`
- `SwitchBoard`
- managed private projects
- `SourceRegistry`
- `PlatformDeployment`
- `Warehouse`

Expected source materials:

- README files
- architecture docs
- verification summaries
- protocol docs
- schema comments
- topology docs
- governance docs

## Deliverables

### D1. Canonical repo pages

Replace the current high-level repo pages with repo-derived material for:

- `OperationsCenter`
- `CxRP`
- `RxP`
- `PlatformManifest`
- private topology repositories
- `Custodian`
- `ExecutorRuntime`
- `SwitchBoard`
- managed private projects

Each page should include:

- mission
- what this repo is
- what this repo is not
- ownership boundaries
- integration points
- public-safe diagrams

### D2. Generated public-safe contract surface

Add generated or semi-generated pages for:

- schema indexes
- enum indexes
- vocabulary indexes
- compatibility tables

These belong under `generated/` and should be derived from canonical owners,
not hand-maintained duplicates.

### D3. Publication workflow

Add CI or GitHub Pages publication wiring so the site can be built and published
from the repository directly.

Minimum deliverables:

- docs build job
- publish job
- build failure on broken navigation or markdown references

### D4. Diagram enrichment

Add public-safe diagrams for:

- control-plane boundaries
- protocol boundaries
- manifest projection flow
- execution sequence
- repo constellation

### D5. Cross-linking

Add source-aware cross-links between:

- overview pages
- repo pages
- protocol pages
- glossary and ontology pages

## Acceptance Criteria

This slice is complete when:

- repo pages use extracted or normalized canonical material instead of only first-pass summaries
- generated contract and vocabulary pages exist
- the site builds in CI
- the site has a publish path
- diagrams cover the main ecosystem boundary surfaces
- cross-links make the site navigable without repo-by-repo reverse engineering

## Non-Goals

This slice does not:

- publish private topology
- duplicate private operational docs
- redefine protocol ownership
- move runtime or orchestration logic into the docs repo
- make the docs repo a runtime dependency

## Follow-on Slices

Likely follow-on work after this slice:

- automated extraction tooling
- versioned protocol docs
- generated topology maps
- generated audit summaries
