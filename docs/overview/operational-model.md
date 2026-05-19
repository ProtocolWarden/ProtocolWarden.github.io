# Operational Model

At a high level:

1. work intent enters through human or system-facing surfaces
2. OperationsCenter plans and governs work
3. SwitchBoard selects a lane and backend
4. Backend adapters perform execution (TeamExecutor/DAGExecutor/CritiqueExecutor for AI topologies; DirectLocal/AiderLocal via ExecutorRuntime subprocess layer for single-agent tasks)
5. artifacts, evidence, and traces are retained
6. Custodian and governance surfaces validate policy and drift boundaries
7. public-safe outputs are documented or projected separately

This model keeps execution, governance, topology, and documentation distinct.
