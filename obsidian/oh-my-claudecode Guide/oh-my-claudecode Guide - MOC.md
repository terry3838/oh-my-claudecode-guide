# oh-my-claudecode Guide - MOC

> [!info]
> output mode: hybrid  
> repo guide: `oh-my-claudecode-guide/`  
> upstream basis: `fae376508355fb03ea6a2477453f37f0a59e707f`

## What this vault set is for

This note set turns OMC into a vault-native learning surface.

Its job is to help you:
- identify what OMC really is
- find the right reading order fast
- separate orchestration from runtime
- separate runtime from integration
- keep repo evidence attached to your study notes

## One-line summary

**OMC is best understood as a Claude Code orchestration runtime with Team, tmux CLI workers, hooks/state, observability, and OpenClaw routing.**

## Start here

1. [[01 Overview]]
2. [[02 Learning Paths]]
3. [[03 Glossary]]
4. [[Concepts/Team vs omc team]]
5. [[Concepts/Team Runtime Deep Dive]]
6. [[Concepts/Hooks and State]]
7. [[Concepts/OpenClaw and Observability]]
8. [[References/Source Map]]

## Reading graph

```mermaid
flowchart LR
    A[[01 Overview]] --> B[[02 Learning Paths]]
    B --> C[[03 Glossary]]
    C --> D[[Concepts/Team vs omc team]]
    D --> E[[Concepts/Team Runtime Deep Dive]]
    E --> F[[Concepts/Hooks and State]]
    F --> G[[Concepts/OpenClaw and Observability]]
    G --> H[[References/Source Map]]
```

## Note map by purpose

### Frontdoor
- [[01 Overview]]
- [[02 Learning Paths]]
- [[03 Glossary]]

### Concepts
- [[Concepts/Team vs omc team]]
- [[Concepts/Team Runtime Deep Dive]]
- [[Concepts/Hooks and State]]
- [[Concepts/OpenClaw and Observability]]

### Workflows
- [[Workflows/Recommended Reading Flow]]

### References
- [[References/Source Map]]

## What to keep in mind while reading

> [!warning]
> README, Migration, Architecture, and Reference do not always expose the exact same counts or emphasis. Read them as different surfaces, not as perfectly synchronized copies.

Key drift examples:
- agent count mismatch across docs
- skill count mismatch across docs
- install-path wording mismatch across docs
- Team current surface vs migration/deprecation wording

## Repo guide links

- repo frontdoor: `README.md`
- repo ↔ note mapping: `OBSIDIAN-VAULT-MAP.md`
