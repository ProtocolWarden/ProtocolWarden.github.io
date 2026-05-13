---
architecture_status: CURRENT
canonical: true
supersedes: []
superseded_by: null
---

# Semantic Federation

Semantic federation is the cross-repo governance gate that keeps the RepoGraph
architecture durable after the migration and hardening passes.

## What it verifies

- RepoGraph importability
- schema compatibility
- projection profile safety
- boundary artifact validity
- ownership drift
- duplicate graph vocabulary
- legacy path regression

## Local execution

Use the `Custodian` governance gate against a workspace root and a materialized
boundary artifact:

```bash
custodian-repograph-governance-gate \
  --repo-root /path/to/workspace \
  --boundary-artifact /path/to/boundary_disclosure_artifact.json \
  --json-out /tmp/repograph-governance.json \
  --summary-out /tmp/repograph-governance.md
```

## CI execution

`Custodian`'s `semantic-federation.yml` workflow materializes the boundary
artifact into a temporary file, checks out the public repo set, and runs the
same gate in GitHub Actions.

## Inputs

- a materialized RepoGraph boundary artifact file
- a workspace root containing the public repos under test

## Failure interpretation

- missing boundary artifact: setup error, fail closed
- malformed artifact: export or transport error, fail closed
- ownership drift / duplicate vocabulary: RepoGraph or consumer regression
- legacy path regression: a forbidden compatibility path reappeared

## Policy split

The public-surface catalog policy is separate from privacy detection:

- `custodian.policy.public_surface_catalog` governs browseable repo pages
- privacy detectors govern leakage, forbidden names, and boundary validity
- architecture docs may still name `PrivateManifest` when describing private
  truth, but the public catalog may not promote it to a first-class repo page

This workflow is operational glue only. It does not define graph semantics or
boundary policy. It preserves the enforcement boundary by consuming the same
artifact file as local operators and CI.
