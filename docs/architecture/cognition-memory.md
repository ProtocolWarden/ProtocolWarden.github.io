# Cognition & Memory Model

How agent sessions across the platform remember things — what persists, what
doesn't, how knowledge travels between machines, and how lessons learned feed
back into future sessions. The canonical deep version of this page lives in PlatformManifest's
architecture docs (the cognition-memory overview); this is the simplified
public map.

## The core idea

Agent sessions do not keep their own long-term state. Each session **anchors**
to a *cognition host* (a manifest repo) and reads its context from a small set
of **tiers**. In-flight session state is scratch — machine-local and
disposable. Anything worth keeping must graduate into a durable tier, and git
is the only transport that moves durable state between machines.

> **Invariant:** a session file never holds the only copy of anything worth
> keeping. Continuity is carried by commits, not by session state.

## Anchoring

ContextLifecycle provides the anchor: `cl session start` resolves the repo's
*owning manifest* and exports `CL_ANCHOR`. Hooks in anchor-dependent repos
(e.g. OperationsCenter) refuse to operate without it and resolve all their
cognition state from the anchoring manifest — those repos deliberately host no
context state of their own. Most repos need no anchoring at all.

## The tiers

| Tier | What it holds | Persistence | Syncs between machines? |
|---|---|---|---|
| **Hot** | compiled startup context (active task, guidelines, recent log) | regenerated at every launch | regenerated per machine from tracked sources |
| **Console truth** | `.console/` task / guidelines / backlog / log | tracked in git | yes — git |
| **Warm** | injectable convention docs (`docs/inject/`) + routing rules | tracked in git | yes — git |
| **Cold** | manually sealed micro-insights (`.context/knowledge/`) | tracked in git | yes — git |
| **Session** | capsules, leases, checkpoints | machine-local, gitignored | never |

## The knowledge lifecycle

The feedback loop that turns one session's lesson into every future session's
default behaviour:

```
session works
  → narrative captured in .console/log.md          (size-capped by audit)
  → reconciliation distills it: a gate refuses to
    prune history that isn't documented in real docs
  → recurring conventions become injectable leaf docs
  → future sessions editing matching paths get those
    conventions injected automatically, pre-edit
```

Every step is enforced by detectors rather than convention: an audit fails
when a console log outgrows its budget (forcing distillation), the
reconciliation gate blocks pruning undocumented work, and a boundary detector
keeps private names off public surfaces. All platform repos are reconciled and
enforcing.

## What deliberately doesn't exist

- **Cross-machine session continuity** — machines share work through commits;
  session state never syncs.
- **Automated insight capture** — an earlier design auto-captured session
  insights into the cold store; it was retired once the console-log pipeline
  proved to do that job better. The cold store remains as a manual surface.
- **A platform-wide injection tier** — injection is per-repo today; the
  cross-repo case is recorded and deferred until demand is demonstrated.

## Related pages

- [ContextLifecycle](../repos/contextlifecycle.md) — the engine: tiered
  memory, anchoring, reconciliation tooling
- [Custodian](../repos/custodian.md) — the detectors that enforce the
  lifecycle (size budgets, boundary, reconciliation gates)
- [Sync & Data Transport](sync-and-data-transport.md) — what the data sync
  layer carries (and that it carries no cognition state)
