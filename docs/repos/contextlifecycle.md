# ContextLifecycle

## Mission

Generic configurable cognition lifecycle runtime for bounded, resumable agent sessions.

## What it does

ContextLifecycle solves the problem of operational agent loops becoming immortal cognition sinks — accumulating context, running forever, and decaying in instruction fidelity over time.

It provides:

- **Core schemas** — `InvestigationCapsule`, `LoopCheckpoint`, `WorkerHandoff`, combined `worker_scope`/`lease`
- **`.context/` surface** — per-repo durable cognition state directory
- **ContextGuard** — runtime-neutral lifecycle enforcement engine with adapter-specific implementations
- **Context injection (tiered memory)** — a routing engine that injects the relevant project conventions and surfaces durable findings *at edit time* (see below)
- **Runtime adapters** — Claude Code (included), Codex/Aider/subprocess (extensible)
- **Presets** — ready-to-use configs for audit sitters, watchdog loops, and CI investigators

## Context injection (tiered memory)

Beyond enforcing the session boundary, ContextLifecycle keeps a project's
durable knowledge in front of the agent — pushed, not searched-for — across
three tiers:

- **Warm** — a glob → leaf-doc routing table (`routes.yaml`). On a Write/Edit,
  the pre-tool hook injects the matching convention docs as the model's
  pre-edit context, within a budget.
- **Cold** — `.context/knowledge/` durable findings. The same routing pass
  surfaces matching findings as a one-line index (so cold is never write-only),
  expandable on demand.
- **Consolidation** — a promotion pass distills cold → warm under a
  *consequence veto* (a finding is only promoted once it was acted on and
  survived — landed in a commit with tests green), with usage-decay and pinning
  for high-stakes, rarely-touched knowledge.

The engine ships in the package and is laid into a repo by **`cl context init`**
(scaffolds `routes.yaml`, `docs/inject/`, `.context/knowledge/`, and the engine
into `.context/.engine/`); the Claude hook adapters call it by path. Activation
is gated by a config flag and the injection block can never block a tool call.

## What it does NOT do

- It is not an execution engine (that is OperationsCenter)
- It is not a routing system for *execution* (that is SwitchBoard)
- It is not a conversation memory service — tiered memory is durable *project*
  knowledge (conventions, findings), not chat history
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
