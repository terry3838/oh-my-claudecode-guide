# Upstream Snapshot — oh-my-claudecode

- source repo: `https://github.com/Yeachan-Heo/oh-my-claudecode.git`
- previous synced commit: `e3509365cfc264228c68c417d39c45d5b4df70cb`
- current synced commit: `2487d3878f8d25e60802940b020d5ee8774d135e`
- sync mode: `update`
- impact labels: 설치/설정, CLI/명령어, 문서 구조, 스킬/플러그인, 소스코드, 테스트/검증
- guide repo: `oh-my-claudecode-guide`

## 원본 한줄 요약

English | [한국어](README.ko.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Español](README.es.md) | [Tiếng Việt](README.vi.md) | [Português](README.pt.md)

## recent upstream commits

- `2487d387 Merge pull request #2162 from Yeachan-Heo/release/4.10.2`
- `1fe4f160 Unblock the 4.10.2 release path`
- `81d153ef Merge pull request #2146 from Yeachan-Heo/issue-2143-omc-launch-followup`
- `42b92f6f feat(hud): add configurable call count icon format (#2151)`
- `80d1cae2 fix: resolve global HUD npm package lookup outside Node projects (#2149)`
- `25f3e2de fix: force-load omc claude config on omc launch`
- `0d836e64 fix: preserve existing global CLAUDE.md during setup (#2144)`
- `954f998a Preserve team worker pane width and bundled agent path resolution (#2137)`

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
- `.github/CLAUDE.md`
- `.github/release-body.md`
- `.github/workflows/pr-check.yml`
- `.gitignore`
- `CHANGELOG.md`
- `bridge/cli.cjs`
- `bridge/mcp-server.cjs`
- `bridge/runtime-cli.cjs`
- `bridge/team-mcp.cjs`
- `bridge/team.js`
- `dist/__tests__/bedrock-lm-suffix-hook.test.js`
- `dist/__tests__/bedrock-lm-suffix-hook.test.js.map`
- `dist/__tests__/hud-marketplace-resolution.test.js`
- `dist/__tests__/hud-marketplace-resolution.test.js.map`
- `dist/__tests__/hud/call-counts.test.js`
- `dist/__tests__/hud/call-counts.test.js.map`
- `dist/__tests__/hud/git.test.js`
- `dist/__tests__/hud/git.test.js.map`

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
