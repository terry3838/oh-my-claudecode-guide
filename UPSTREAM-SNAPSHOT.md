# Upstream Snapshot — oh-my-claudecode

- source repo: `https://github.com/Yeachan-Heo/oh-my-claudecode.git`
- guide repo: `oh-my-claudecode-guide`
- previous synced commit: `fae376508355fb03ea6a2477453f37f0a59e707f`
- current synced commit: `fae376508355fb03ea6a2477453f37f0a59e707f`
- sync mode: `no-change`
- impact labels: `docs drift awareness`, `team runtime`, `OpenClaw integration`, `observability`

---

## Executive read

이번 snapshot의 핵심은 “업스트림이 크게 변했다”가 아니라,
**현재 OMC를 설명할 때 어떤 축을 전면에 둬야 하는지 더 분명해졌다**는 것이다.

즉 변경 파일은 없더라도, 학습 가이드 관점에서 중요한 해석 포인트는 분명하다.

### 지금 기준의 핵심 4축

1. **Team이 canonical orchestration surface다**
2. **`omc team`은 tmux CLI worker runtime이다**
3. **OpenClaw는 공식 signal-based integration surface다**
4. **OMC는 observability / state / replay까지 가진 운영 런타임이다**

---

## Upstream one-line summary

**oh-my-claudecode is no longer best explained as a bag of commands; it is better explained as a Claude Code orchestration runtime with Team, CLI workers, hooks/state, observability, and OpenClaw routing.**

---

## Why this snapshot matters

### 1. README frontdoor is not the whole repo

원본 README는 훌륭한 frontdoor이지만, repo 전체를 대표하진 않는다.

실제로는 아래 축을 같이 봐야 한다.
- `docs/`
- `agents/`
- `skills/`
- `bridge/`
- `src/team/`
- `src/hooks/`
- `src/openclaw/`
- `src/hud/`
- `benchmarks/`, `benchmark/`
- `missions/`

즉 snapshot은 단순 최신 커밋 기록이 아니라,
**guide가 upstream을 얼마나 넓게 읽어야 하는지 보여주는 증거**다.

### 2. current surface and historical surface both matter

현재 권장 경로를 알려면 README만 보면 안 되고,
왜 지금 이렇게 됐는지 이해하려면 `docs/MIGRATION.md`도 같이 봐야 한다.

대표 예시:
- Team canonical surface 강조
- legacy Team MCP runtime deprecation
- `omc team` CLI-first direction 강화

### 3. observability is part of product reality

`docs/PERFORMANCE-MONITORING.md`와 `src/hud/`를 보면,
OMC는 단순 실행 도구가 아니라 **실행 관찰 도구**이기도 하다.

즉 snapshot 해석에 아래를 포함해야 한다.
- Agent Observatory
- Session Replay
- Session-end summaries
- HUD preset

---

## Most important upstream evidence used

### A. `README.md`

확인 포인트:
- Quick Start
- Team canonical surface
- tmux CLI workers
- `/ccg` and `omc ask`
- OpenClaw integration overview
- package naming note

### B. `docs/MIGRATION.md`

확인 포인트:
- Team MCP runtime deprecation
- CLI-first migration direction
- surface rename / consolidation history

### C. `docs/REFERENCE.md`

확인 포인트:
- installation/configuration guidance
- `omc ask`, `omc team`, session commands
- state directory / env vars / hooks
- reference-side counts and current support wording

### D. `docs/ARCHITECTURE.md`

확인 포인트:
- hooks / skills / agents / state 4-part model
- skill layering
- agent lane explanation

### E. `docs/OPENCLAW-ROUTING.md`

확인 포인트:
- normalized `signal` contract
- `routeKey`, `priority`, `phase`
- OpenClaw payload shape

### F. `docs/PERFORMANCE-MONITORING.md`

확인 포인트:
- Agent Observatory
- Session Replay
- session-end summary / HUD guidance
- live/runtime inspection posture

---

## Drift and ambiguity to keep visible

좋은 가이드는 아래 차이를 숨기지 않아야 한다.

| Topic | Evidence | Guide implication |
|---|---|---|
| Agent count | README: `32 specialized agents` / Architecture: `19 specialized agents` | 문서 기준선이 하나로 고정돼 있지 않다 |
| Skill count | Reference: `32 total` / Architecture: `31 total` / Migration: `37 core skills` | 버전대/문맥별 count mismatch를 밝히고 읽어야 한다 |
| Install guidance | README shows plugin + npm path / Reference says plugin-only supported | 학습자에게 “현재 권장 경로”와 “역사적/보조 경로”를 분리해 설명해야 한다 |
| Team runtime | README explains current surface / Migration explains deprecation and CLI-only shift | current reality는 둘을 같이 봐야 선명해진다 |

---

## Recent upstream commits

최근 커밋은 대규모 구조 변경이라기보다 현재 라인을 정리하는 성격이 강하다.

- `fae37650` — chore: update Discord invite link to OmO (Ultraworkers) server
- `0ec792c0` — chore: gitignore release-body.md to prevent stale release notes
- `f93e27bc` — fix(release): add version sync hook + fix stale release body
- `8660d291` — fix(ci): sync version markers to 4.9.3
- `884ec78d` — chore: bump version to 4.9.3
- `cc71a7db` — fix: outbox reader partial lines
- `88d6a044` — fix: team-status tmux provider

### snapshot reading

이 커밋 목록이 시사하는 건 이쪽이다.
- Team/tmux runtime 안정화가 실제 유지보수 축이다.
- release/version consistency도 중요하게 다뤄진다.
- 문서/배포/운영 모두를 다루는 repo라는 사실이 계속 유지된다.

---

## Top-level structure that matters for guides

- `.claude-plugin/`
- `.mcp.json`
- `agents/`
- `benchmark/`
- `benchmarks/`
- `bridge/`
- `docs/`
- `examples/`
- `hooks/`
- `missions/`
- `src/`

### guide implication

guide는 최소한 다음을 동시에 반영해야 한다.
- frontdoor usage
- architecture explanation
- runtime / operator surfaces
- integration surfaces
- observability / evaluation posture

---

## What changed in the guide because of this snapshot

이번 snapshot 해석을 반영해서 guide는 아래 방향으로 강화됐다.

1. `README.md` frontdoor를 repo breadth 중심으로 다시 세움
2. `01-learning-paths.md`를 reader-track 기반으로 재구성
3. `02-glossary.md`를 층위 구분 중심으로 재구성
4. OpenClaw / runtime / observability를 부록이 아니라 핵심 축으로 끌어올림
5. drift examples를 숨기지 않고 전면 배치

---

## Snapshot judgment

현재 upstream 기준으로 가장 정확한 판단은 이거다.

> **OMC는 Claude Code용 멀티 에이전트 orchestration runtime이며, 지금 읽어야 할 중심축은 Team, tmux CLI workers, hooks/state, observability, and OpenClaw routing이다.**

변경 파일이 없더라도,
이 판단은 guide 품질을 끌어올리는 데 충분히 중요한 snapshot이다.
