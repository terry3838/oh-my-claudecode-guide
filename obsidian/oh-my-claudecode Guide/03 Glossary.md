# OMC Glossary

> [!info]
> Use this note to separate **role**, **behavior**, **runtime**, and **integration** terms.

## The 6 key distinction axes

1. agent vs skill
2. `/team` vs `omc team`
3. autopilot vs ralph
4. command surface vs runtime surface
5. hook event vs OpenClaw signal
6. README frontdoor vs current repo reality

## Core terms

### Agent
Role-based executor such as planner, executor, architect, critic, verifier.

### Skill
Behavior injection layer that changes how orchestration works.

### Team
Canonical orchestration surface.

### `omc team`
Runtime surface for tmux CLI workers.

### Hooks
Lifecycle injection layer.

### State
Stored execution continuity: sessions, artifacts, replay, notepads.

### OpenClaw signal
Normalized routing contract with fields like `kind`, `phase`, `routeKey`, `priority`.

### Observability
HUD, replay, session summaries, and other ways to inspect live or finished execution.

### Drift
Mismatch in wording, counts, or emphasis across README, Migration, Architecture, and Reference docs.

## Related notes

- [[01 Overview]]
- [[02 Learning Paths]]
- [[Concepts/Team vs omc team]]
- [[Concepts/Hooks and State]]
