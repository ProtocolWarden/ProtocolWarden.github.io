# ContextLifecycle

## Mission

Generic configurable cognition lifecycle runtime for bounded, resumable agent sessions.

## What it does

ContextLifecycle solves the problem of operational agent loops becoming immortal cognition sinks — accumulating context, running forever, and decaying in instruction fidelity over time.

It provides:

- **Core schemas** — `InvestigationCapsule`, `LoopCheckpoint`, `WorkerHandoff`, combined `worker_scope`/`lease`
- **`.context/` surface** — per-repo durable cognition state directory
- **ContextGuard** — runtime-neutral lifecycle enforcement engine with adapter-specific implementations
- **Runtime adapters** — Claude Code (included), Codex/Aider/subprocess (extensible)
- **Presets** — ready-to-use configs for audit sitters, watchdog loops, and CI investigators

## What it does NOT do

- It is not an execution engine (that is OperationsCenter)
- It is not a routing system (that is SwitchBoard)
- It is not a conversation memory service
- It does not own runtime state

## Consuming repos

- **OperationsCenter** — watchdog loop checkpointing, investigation worker dispatch
- Private project repos — audit sitter capsules, gate remediation handoffs (tracked in project-level manifests)

## Boundary

```
schemas    = describe the lifecycle boundary
ContextGuard = enforces the lifecycle boundary
checkpoints  = let the system survive without immortal sessions
```

## Runtime roles

| Component | Role |
|-----------|------|
| `.context/` | durable cognition surface — runtime neutral |
| `.agent/` | generic runtime integration surface |
| `.claude/` | Claude Code adapter implementation |
| ContextGuard | enforcement policy engine |

## Links

- [GitHub](https://github.com/ProtocolWarden/ContextLifecycle)
- [Adoption guide](https://github.com/ProtocolWarden/ContextLifecycle/blob/main/docs/adopting.md)
- [Philosophy](https://github.com/ProtocolWarden/ContextLifecycle/blob/main/docs/philosophy.md)
