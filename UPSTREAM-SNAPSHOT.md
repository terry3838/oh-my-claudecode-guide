# Upstream Snapshot — oh-my-claudecode

- source repo: `https://github.com/Yeachan-Heo/oh-my-claudecode.git`
- previous synced commit: `fae376508355fb03ea6a2477453f37f0a59e707f`
- current synced commit: `fae376508355fb03ea6a2477453f37f0a59e707f`
- sync mode: `no-change`
- impact labels: 일반 변경
- guide repo: `oh-my-claudecode-guide`

## 원본 한줄 요약

English | [한국어](README.ko.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Español](README.es.md) | [Tiếng Việt](README.vi.md) | [Português](README.pt.md)

## recent upstream commits

- `fae37650 chore: update Discord invite link to OmO (Ultraworkers) server`
- `0ec792c0 chore: gitignore release-body.md to prevent stale release notes`
- `f93e27bc fix(release): add version sync hook + fix stale release body`
- `8660d291 fix(ci): sync version markers to 4.9.3`
- `884ec78d chore: bump version to 4.9.3`
- `f9bbb99e Merge remote-tracking branch 'origin/dev'`
- `cc71a7db Merge pull request #1982 from riftzen-bit/fix/outbox-reader-partial-lines`
- `88d6a044 Merge pull request #1981 from riftzen-bit/fix/team-status-tmux-provider`

## top-level structure

- `.claude-plugin/`
- `.eslintignore`
- `.mcp.json`
- `.npmignore`
- `agents/`
- `AGENTS.md`
- `assets/`
- `benchmark/`
- `benchmarks/`
- `bridge/`
- `CHANGELOG.md`
- `CLAUDE.md`
- `dist/`
- `docs/`
- `eslint.config.js`
- `examples/`
- `hooks/`
- `LICENSE`
- `missions/`
- `package-lock.json`

## changed files

- 변경 파일 없음

## README excerpt

```md
English | [한국어](README.ko.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Español](README.es.md) | [Tiếng Việt](README.vi.md) | [Português](README.pt.md)

# oh-my-claudecode

[![npm version](https://img.shields.io/npm/v/oh-my-claude-sisyphus?color=cb3837)](https://www.npmjs.com/package/oh-my-claude-sisyphus)
[![npm downloads](https://img.shields.io/npm/dm/oh-my-claude-sisyphus?color=blue)](https://www.npmjs.com/package/oh-my-claude-sisyphus)
[![GitHub stars](https://img.shields.io/github/stars/Yeachan-Heo/oh-my-claudecode?style=flat&color=yellow)](https://github.com/Yeachan-Heo/oh-my-claudecode/stargazers)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Sponsor](https://img.shields.io/badge/Sponsor-❤️-red?style=flat&logo=github)](https://github.com/sponsors/Yeachan-Heo)
[![Discord](https://img.shields.io/discord/1452487457085063218?color=5865F2&logo=discord&logoColor=white&label=Discord)](https://discord.gg/PUwSMR9XNk)

> **For Codex users:** Check out [oh-my-codex](https://github.com/Yeachan-Heo/oh-my-codex) — the same orchestration experience for OpenAI Codex CLI.

**Multi-agent orchestration for Claude Code. Zero learning curve.**

_Don't learn Claude Code. Just use OMC._

[Get Started](#quick-start) • [Documentation](https://yeachan-heo.github.io/oh-my-claudecode-website) • [CLI Reference](https://yeachan-heo.github.io/oh-my-claudecode-website/docs.html#cli-reference) • [Workflows](https://yeachan-heo.github.io/oh-my-claudecode-website/docs.html#workflows) • [Migration Guide](docs/MIGRATION.md) • [Discord](https://discord.gg/PUwSMR9XNk)

---

## Quick Start

**Step 1: Install**

Marketplace/plugin install (recommended for most Claude Code users):

```bash
/plugin marketplace add https://github.com/Yeachan-Heo/oh-my-claudecode
/plugin install oh-my-claudecode
```

If you prefer the npm CLI/runtime path instead of the marketplace flow:

```bash
npm i -g oh-my-claude-sisyphus@latest
```

**Step 2: Setup**

```bash
/setup
/omc-setup
```

**Step 3: Build something**

```
autopilot: build a REST API for managing tasks
```

That's it. Everything else is automatic.

### Not Sure Where to Start?

If you're uncertain about requirements, have a vague idea, or want to micromanage the design:

```
/deep-interview "I want to build a task management app"
```

The deep interview uses Socratic questioning to clarify your thinking before any code is written. It exposes hidden assumptions and measures clarity across weighted dimensions, ensuring you know exactly what to build before execution begins.

## Team Mode (Recommended)

Starting in **v4.1.7**, **Team** is the canonical orchestration surface in OMC. The legacy `swarm` keyword/skill has been removed; use `team` directly.

```bash
/team 3:executor "fix all TypeScript errors"
```

Team runs as a staged pipeline:

`team-plan → team-prd → team-exec → team-verify → team-fix (loop)`

Enable Claude Code native teams in `~/.claude/settings.json`:

```json
{
  "env": {
    "CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS": "1"
  }
}
```

> If teams are disabled, OMC will warn you and fall back to non-team execution where possible.

### tmux CLI Workers — Codex & Gemini (v4.4.0+)

**v4.4.0 removes the Codex/Gemini MCP servers** (`x`, `g` providers). Use the CLI-first Team runtime (`omc team ...`) to spawn real tmux worker panes:

```bash
omc team 2:codex "review auth module for security issues"
omc team 2:gemini "redesign UI components for accessibility"
omc team 1:claude "implement the payment flow"
omc team status auth-review
omc team shutdown auth-review
```

`/omc-teams` remains as a legacy compatibility skill and now routes to `omc team ...`.

For mixed Codex + Gemini work in one command, use the **`/ccg`** skill (routes via `/ask codex` + `/ask gemini`, then Claude synthesizes):

```bash
/ccg Review this PR — architecture (Codex) and UI components (Gemini)
```

| Surface                   | Workers            | Best For                                     |
| ------------------------- | ------------------ | -------------------------------------------- |
| `omc team N:codex "..."`  | N Codex CLI panes  | Code review, security analysis, architecture |
| `omc team N:gemini "..."` | N Gemini CLI panes | UI/UX design, docs, large-context tasks      |
| `omc team N:claude "..."` | N Claude CLI panes | General tasks via Claude CLI in tmux         |
| `/ccg`                    | /ask codex + /ask gemini | Tri-model advisor synthesis           |

Workers spawn on-demand and die when their task completes — no idle resource usage. Requires `codex` / `gemini` CLIs installed and an active tmux session.

> **Note: Package naming** — The project is branded as **oh-my-claudecode** (repo, plugin, commands), but the npm package is published as [`oh-my-claude-sisyphus`](https://www.npmjs.com/package/oh-my-claude-sisyphus). If you install or upgrade the CLI tools via npm/bun, use `npm i -g oh-my-claude-sisyphus@latest`.

### Updating
```
