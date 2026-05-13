---
architecture_status: CURRENT
canonical: true
supersedes: []
superseded_by: null
---

# RepoGraph Post-PASS Hardening Baseline

This page records the known-good architectural checkpoint reached after the
RepoGraph migration, hardening, stability, and semantic-federation passes.

## Baseline guarantees

- RepoGraph remains the canonical graph language and semantic governance owner.
- private-truth layer remains the owner of private graph truth and boundary artifact generation.
- PlatformManifest remains the public graph projection publisher.
- Custodian remains fail-closed and consumes boundary artifacts only.
- OperationsCenter remains an orchestration consumer of composed graph truth.
- PlatformDeployment remains deployment/topography overlay only.
- Warehouse remains a context packaging utility only.

## Enforced invariants

- `REPOGRAPH_BOUNDARY_ARTIFACT_FILE` is required for Custodian enforcement.
- Missing or malformed boundary artifacts fail closed.
- Projection profiles remain explicit and validated.
- Schema governance remains versioned and fail-closed.
- Drift detection remains machine-readable and part of the federation gate.

## Intentionally deferred

- cryptographic signing infrastructure
- trust-chain and key-management system
- full explorer implementation
- policy-plane expansion
- advanced topography modeling
- multi-environment deployment semantics
- UI visualization systems

## Future change requirements

Any future semantic change in RepoGraph requires explicit schema-governance
review. In particular:

- new enum values require a version bump
- removed enum values are breaking
- boundary artifact field removal is breaking
- projection rule removal is breaking
- projection safety downgrades are breaking unless explicitly declared and reviewed

This checkpoint is a baseline marker, not a new architecture layer.
