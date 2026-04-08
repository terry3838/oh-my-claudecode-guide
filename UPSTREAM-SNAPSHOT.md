# Upstream Snapshot — oh-my-claudecode

- source repo: `https://github.com/Yeachan-Heo/oh-my-claudecode.git`
- previous synced commit: `2487d3878f8d25e60802940b020d5ee8774d135e`
- current synced commit: `823f59ba4dfe3efd3518d99ad83156a11cdcb7b5`
- sync mode: `update`
- impact labels: README/소개, 설치/설정, CLI/명령어, 스킬/플러그인, 테스트/검증
- guide repo: `oh-my-claudecode-guide`

## 원본 한줄 요약

English | [한국어](README.ko.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Español](README.es.md) | [Tiếng Việt](README.vi.md) | [Português](README.pt.md)

## recent upstream commits

- `823f59ba chore(release): bump version to v4.11.1`
- `3e80dac6 fix(installer): use getPackageDir() instead of __dirname for HUD helper copies (#2347)`
- `ec9398d7 Merge pull request #2331 from shaun0927/fix/hardmax-iterations-bypass`
- `9b340a8a fix(security): clamp hardMaxIterations and enforce in autopilot`
- `d716a30d Merge pull request #2247 from pgagarinov/feat/hud-git-status`
- `e3b04e45 Merge pull request #2333 from shaun0927/fix/team-registration-locks`
- `cb653014 feat(hud): add git working tree status element`
- `d671cecb fix(team): wrap withFileLockSync in try/catch for lock contention safety`

## top-level structure

- `.claude-plugin/`
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
- `package.json`

## changed files

- `.claude-plugin/marketplace.json`
- `.claude-plugin/plugin.json`
- `.github/release-body.md`
- `.github/workflows/release.yml`
- `CHANGELOG.md`
- `README.md`
- `bridge/cli.cjs`
- `bridge/mcp-server.cjs`
- `bridge/runtime-cli.cjs`
- `bridge/team-bridge.cjs`
- `bridge/team-mcp.cjs`
- `bridge/team.js`
- `dist/__tests__/auto-update.test.js`
- `dist/__tests__/auto-update.test.js.map`
- `dist/__tests__/cli-config-stop-callback.test.js`
- `dist/__tests__/cli-config-stop-callback.test.js.map`
- `dist/__tests__/delegation-enforcement-levels.test.js`
- `dist/__tests__/delegation-enforcement-levels.test.js.map`
- `dist/__tests__/doctor-conflicts.test.js`
- `dist/__tests__/doctor-conflicts.test.js.map`

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

## Core Maintainers

| Role | Name | GitHub |
| --- | --- | --- |
| Creator & Lead | Yeachan Heo | [@Yeachan-Heo](https://github.com/Yeachan-Heo) |
| Maintainer | HaD0Yun | [@HaD0Yun](https://github.com/HaD0Yun) |

## Ambassadors

| Name | GitHub |
| --- | --- |
| Sigrid Jin | [@sigridjineth](https://github.com/sigridjineth) |

## Top Collaborators

| Name | GitHub |
| --- | --- |
| riftzen-bit | [@riftzen-bit](https://github.com/riftzen-bit) |
| Seunggwan Song | [@nathan-song](https://github.com/nathan-song) |
| JunghwanNA | [@shaun0927](https://github.com/shaun0927) |
| Junho Yeo | [@junhoyeo](https://github.com/junhoyeo) |
| Alex Urevick-Ackelsberg | [@AlexUrevick](https://github.com/AlexUrevick) |

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
# Inside a Claude Code / OMC session
/setup
/omc-setup

# From your terminal
omc setup
```

**Step 3: Build something**

```bash
# Inside a Claude Code / OMC session
/autopilot "build a REST API for managing tasks"

# Natural-language in-session shortcut
autopilot: build a REST API for managing tasks
```

That's it. Everything else is automatic.

### CLI Commands vs In-Session Skills

OMC exposes two different surfaces:

- **Terminal CLI commands**: run `omc ...` from your shell after installing the npm/runtime path (`npm i -g oh-my-claude-sisyphus@latest`) or from a local checkout.
- **In-session skills**: run `/...` inside a Claude Code session after installing the plugin/setup flow.

| Feature | Terminal CLI | In-session skill | Notes |
| --- | --- | --- | --- |
| Setup | `omc setup` | `/setup` or `/omc-setup` | Both are real entrypoints. `/setup` is the easiest plugin-first path. |
| Ask providers | `omc ask codex "review this patch"` | `/ask codex "review this patch"` | Both route through the same advisor flow. |
| Team orchestration | `omc team 2:codex "review auth flow"` | `/team 3:executor "fix all TypeScript errors"` | Both exist, but they are different runtimes: `omc team` launches tmux CLI workers; `/team` runs the in-session native team workflow. |
| Autopilot / Ralph / Ultrawork / Deep Interview | — | `/autopilot ...`, `/ralph ...`, `/ultrawork ...`, `/deep-interview ...` | These are in-session skills. There is no `omc autopilot` / `omc ralph` / `omc ultrawork` CLI subcommand in this repo. |
| Autoresearch | `omc autoresearch ...` | `/deep-interview --autoresearch ...` | `omc autoresearch` is the real CLI command. The in-session path is the setup/interview lane that helps you launch it. |

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

Use `/team ...` when you want Claude Code's in-session native team workflow. Use `omc team ...` when you want terminal-launched tmux CLI workers (`claude` / `codex` / `gemini` panes).

Team runs as a staged pipeline:
```
