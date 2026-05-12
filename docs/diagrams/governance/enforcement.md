# Governance Enforcement

```mermaid
graph TD
    Change[Change or Generated Output]
    Policy[Invariant and Policy Rules]
    Custodian[Custodian]
    Review[Human Review]
    Release[Release or Publication]

    Change --> Policy
    Policy --> Custodian
    Custodian --> Review
    Review --> Release
```
