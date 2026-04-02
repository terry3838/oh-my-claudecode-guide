# 01 Overview

[[oh-my-claudecode Guide - MOC]]

## What OMC is

OMC is not best understood as a bag of helpful commands.

It is better understood as a **Claude Code runtime layer** that adds:
- Team orchestration
- persistent execution styles such as Ralph
- tmux CLI worker operation via `omc team`
- hooks and state
- observability via HUD / replay / summaries
- notifications and OpenClaw routing

## Why this matters

This framing changes how you read the repo.

Without it, the project looks like:
- commands
- keywords
- setup steps

With it, the project looks like:
- orchestration
- runtime control
- state continuity
- external routing
- monitoring and evaluation

## The first four things to lock in

1. Team is the current canonical orchestration surface.
2. `omc team` is the runtime/operator surface.
3. package naming differs from repo branding.
4. OpenClaw is an official integration surface, not an afterthought.

## Read next

- [[02 Learning Paths]]
- [[03 Glossary]]
- [[Concepts/Team vs omc team]]
- [[Concepts/Hooks and State]]
