# oh-my-claudecode (OMC) 학습 가이드

> Claude Code 위에 team orchestration, tmux worker runtime, hooks/state, HUD, OpenClaw routing을 얹는 운영 런타임

OMC는 지금 “slash command가 많은 플러그인”으로 읽으면 좁아요. 현재 README와 최근 문서 변화는 더 분명해요.

- **plugin 설치 경로와 npm CLI 경로가 공존해요**
- **`/team`과 `omc team`은 관련 있지만 다른 표면이에요**
- **Team이 canonical orchestration surface예요**
- **`--plugin-dir-mode` 같은 운영 플래그를 이해해야 설치 중복을 피할 수 있어요**

이 가이드는 그 현재 기준을 frontdoor에 다시 올려요.

## 버전 기준

- upstream 기준 커밋: `7b4a9e04`
- current version: `4.11.4`
- 근거: `README.md`, `CHANGELOG.md`, `package.json`, top-level 구조

## OMC를 한 문장으로 보면

**Claude Code 세션 안쪽의 skill 표면과, 바깥의 `omc` CLI/runtime 표면을 함께 제공하면서 Team, state, hooks, HUD, OpenClaw routing까지 운영하는 Claude Code runtime**이에요.

## 지금 가장 중요한 메시지

### 1. plugin 경로와 npm CLI 경로를 같이 이해해야 해요

README는 지금 두 경로를 같이 보여줘요.

- marketplace/plugin 설치
- npm CLI/runtime 설치

즉 OMC는 “plugin only”로 읽기보다,
**plugin surface와 terminal runtime surface가 공존하는 시스템**으로 보는 편이 맞아요.

### 2. `--plugin-dir-mode`를 모르면 설치가 중복될 수 있어요

`omc --plugin-dir <path>`나 `claude --plugin-dir <path>`로 돌릴 때는
`omc setup --plugin-dir-mode` 또는 `OMC_PLUGIN_ROOT`를 같이 이해해야 해요.
이건 사소한 플래그가 아니라 **plugin이 제공하는 skills/agents와 runtime 설치가 충돌하지 않게 하는 운영 계약**이에요.

### 3. `/team`과 `omc team`을 구분해야 해요

- `/team`: Claude Code 안에서 쓰는 in-session canonical team surface
- `omc team`: tmux에서 real claude/codex/gemini worker를 띄우는 CLI runtime surface

둘은 이어져 있지만 같은 명령의 다른 문법이 아니에요.

### 4. Team이 현재 canonical orchestration surface예요

README는 `v4.1.7` 이후 Team을 중심 orchestration으로 분명히 둬요.
즉 지금 OMC를 배울 때는 Team pipeline을 먼저 이해하는 편이 맞아요.

## 추천 읽기 순서

1. `sections/01-overview.md`
2. `01-learning-paths.md`
3. `sections/02-team-runtime-and-worker-model.md`
4. `sections/03-hooks-openclaw-and-observability.md`
5. `02-glossary.md`

## 가장 현실적인 첫 성공 루프

plugin 사용자라면:
```bash
/plugin marketplace add https://github.com/Yeachan-Heo/oh-my-claudecode
/plugin install oh-my-claudecode
/setup
/omc-setup
```

CLI/runtime 사용자라면:
```bash
npm i -g oh-my-claude-sisyphus@latest
omc setup
```

그 다음:
```text
/autopilot "build a REST API for managing tasks"
/team 3:executor "fix all TypeScript errors"
```

운영자 표면이 필요할 때:
```bash
omc team 2:codex "review auth flow"
omc team status <team-name>
```

## 자주 생기는 오해

- **오해 1: `/team`과 `omc team`은 같은 표면이다**
  - 아니에요. in-session surface와 CLI runtime surface가 달라요.

- **오해 2: plugin 설치만 알면 된다**
  - 아니에요. 지금 README는 plugin과 npm CLI 경로를 함께 설명해요.

- **오해 3: `--plugin-dir-mode`는 선택적 사소 옵션이다**
  - 아니에요. plugin-dir 기반 운영에서 중복 설치를 막는 핵심 계약이에요.

## 누가 먼저 읽으면 좋나

- Claude Code 위에 팀 실행, hooks, HUD, state를 함께 이해하고 싶은 사람
- plugin 설치와 CLI 설치를 같이 운영하는 사람
- OpenClaw routing이나 tmux worker runtime까지 연결해서 보려는 운영자

## 다음 행동

- 처음이면 `01-learning-paths.md`부터 읽고 `/team`과 `omc team`을 먼저 구분하세요.
- 운영자면 `sections/03-hooks-openclaw-and-observability.md`를 먼저 보세요.

<!-- GUIDE_SYNC:START -->
## 자동 동기화 상태

- origin repo: `oh-my-claudecode`
- latest source commit: `09ffccc55803`
- sync mode: `no-change`
- 영향 분류: 일반 변경

### 이번 반영 포인트

이번 싸이클에서는 origin 변경이 없어 guide 본문은 유지했고, 동기화 기준점만 재확인했습니다.

### 최근 upstream 커밋

- `09ffccc5 Fix explicit /ralplan startup stalling before planning (#2624)`
- `cf06566d Merge dev for v4.11.6 release`
- `28756531 chore(release): bump version to v4.11.6`
- `74edf7c2 Merge pull request #2604 from Yeachan-Heo/omx/issue-2602-ralph-prd-architect-gate`
- `f6507966 Close Ralph approval spoofing in reviewer-gated progression`
- `e122fcf0 Prevent Ralph from approving its own injected prompt text`

### 변경 파일 샘플

- 이번 싸이클에서는 신규 변경 파일이 없습니다.

> 이 블록은 guide sync가 자동 갱신합니다.
<!-- GUIDE_SYNC:END -->
