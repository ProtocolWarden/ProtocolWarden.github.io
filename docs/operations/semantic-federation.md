---
architecture_status: CURRENT
canonical: true
supersedes: []
superseded_by: null
---

# Semantic Federation

Semantic federation is the cross-repo regression gate that keeps the RepoGraph
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

Use the `Custodian` migration gate against a workspace root and a materialized
boundary artifact:

```bash
custodian-repograph-migration-gate \
  --repo-root /path/to/workspace \
  --boundary-artifact /path/to/boundary_disclosure_artifact.json \
  --json-out /tmp/repograph-federation.json \
  --summary-out /tmp/repograph-federation.md
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

This workflow is operational glue only. It does not define graph semantics or
boundary policy. It preserves the enforcement boundary by consuming the same
artifact file as local operators and CI.
