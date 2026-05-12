# Execution Objects

Core execution-related objects include:

- `TaskProposal`
- `LaneDecision`
- `ExecutionRequest`
- `ExecutionResult`
- `RuntimeBinding`
- `CapabilitySet`

## Ownership

- `TaskProposal`, `LaneDecision`, `ExecutionRequest`, `ExecutionResult`,
  `RuntimeBinding`, `CapabilitySet`: canonical wire semantics belong in `CxRP`
- runtime invocation and return details belong in `RxP`
- stricter internal orchestration models may exist in consumer repos, but they
  must map explicitly to canonical contracts
