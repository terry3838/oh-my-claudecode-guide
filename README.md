# oh-my-claudecode(OMC) 학습 가이드

**Claude Code 위에 얹는 멀티 에이전트 오케스트레이션 런타임을, 학습자 기준으로 다시 정리한 가이드**

---

## 이 가이드는 무엇인가

이 저장소는 원본 [`oh-my-claudecode`](https://github.com/Yeachan-Heo/oh-my-claudecode)를 그대로 번역하거나 요약한 문서가 아니다. 원본 README, 주요 docs, 실제 소스 디렉터리를 함께 확인해서 **처음 배우는 사람이 어디서 시작해야 하는지** 보이도록 다시 짠 학습 가이드다.

이 가이드가 답하려는 질문은 네 가지다.

1. **OMC가 정확히 무엇인가**
2. **Claude Code 단독 사용과 무엇이 다른가**
3. **지금 기준에서 어디서부터 배우는 게 맞는가**
4. **원본 repo를 읽을 때 어느 경로가 핵심인가**

---

## 한눈에 보는 OMC

### 한 줄 정의

**OMC는 Claude Code 위에 팀 실행, 검증 루프, tmux worker 운영, hooks, 상태 저장, 외부 게이트웨이 연동을 추가하는 운영 런타임이다.**

### Claude Code와의 차이

| 구분 | Claude Code 단독 | OMC 사용 |
|---|---|---|
| 기본 실행 단위 | 한 세션, 한 에이전트 중심 | 여러 역할/단계를 조율하는 orchestration 중심 |
| 완료 기준 | 대화 단위로 끝나기 쉬움 | verify/fix 루프까지 포함 가능 |
| 팀 실행 | 제한적/기본 기능 의존 | `team`, `omc team`, staged pipeline 중심 |
| 운영 가시성 | 상대적으로 얇음 | HUD, tmux panes, artifacts, session state |
| 확장 포인트 | 기본 프롬프트/설정 중심 | hooks, skills, notifications, OpenClaw 연동 |

### 누가 배우면 좋은가

- Claude Code는 이미 써봤지만 **큰 작업을 더 체계적으로 굴리고 싶은 사람**
- 단일 에이전트보다 **계획 → 실행 → 검증 흐름**이 중요한 사람
- Codex / Gemini / Claude를 섞는 **멀티 모델 운영**에 관심 있는 사람
- hooks, tmux, OpenClaw까지 포함한 **실전 운영 레이어**를 이해하고 싶은 사람

---

## 버전 기준과 확인 범위

### 이 가이드의 기준점

- 원본 repo: `https://github.com/Yeachan-Heo/oh-my-claudecode.git`
- 확인한 최신 기준 커밋: `fae376508355fb03ea6a2477453f37f0a59e707f`
- npm package: `oh-my-claude-sisyphus@4.9.3`

### 이번 정리에 실제로 반영한 근거

- 원본 `README.md`
- 원본 `docs/MIGRATION.md`
- 원본 `docs/ARCHITECTURE.md`
- 원본 `docs/REFERENCE.md`
- 원본 `docs/OPENCLAW-ROUTING.md`
- 원본 `package.json`
- 원본 핵심 디렉터리: `agents/`, `skills/`, `bridge/`, `src/team/`, `src/hooks/`, `src/openclaw/`, `src/notifications/`, `src/hud/`

### 먼저 알아둘 드리프트/주의점

1. **브랜딩 이름과 npm 패키지 이름이 다르다**
   - repo / plugin / 명령어 브랜딩: `oh-my-claudecode`
   - npm package: `oh-my-claude-sisyphus`

2. **설치 경로 설명은 문서마다 결이 조금 다르다**
   - 원본 README는 plugin 경로와 npm 경로를 모두 보여준다.
   - 원본 `docs/REFERENCE.md`는 plugin 방식을 강하게 기본 경로로 설명한다.
   - 그래서 학습자는 **plugin 설치를 기본 경로로 이해하고**, npm 경로는 패키지명 혼동 방지용 보조 정보로 보는 게 안전하다.

3. **Team 관련 표면은 과거 문서와 현재 문서가 섞여 있을 수 있다**
   - 현재 기준 핵심은 `team`
   - legacy `swarm` 사고방식으로 읽으면 구조를 오해하기 쉽다.

---

## 지금 OMC를 배울 때 가장 중요한 5가지

### 1. Team이 canonical orchestration surface다

원본 README는 `v4.1.7` 이후 Team을 기본 표면으로 설명한다.

```text
team-plan → team-prd → team-exec → team-verify → team-fix (loop)
```

핵심은 “여러 명을 띄운다”가 아니라, **계획-실행-검증 생명주기를 묶는다**는 점이다.

### 2. `omc team`은 tmux 기반 CLI worker 운영 표면이다

`v4.4.0+` 이후 README와 migration 문서가 공통으로 강조하는 변화는 이것이다.

- Codex/Gemini MCP runtime 경로는 뒤로 밀리고
- **실제 CLI worker를 tmux pane에서 운영하는 방식**이 더 중요해졌다.

즉 `/team`은 학습자에게 보이는 orchestration 표면이고,
`omc team`은 운영자가 보는 CLI runtime 표면에 가깝다.

### 3. Ralph는 “대충 됨”을 허용하지 않는 완료 집착 모드다

Ralph는 단순 자동 실행이 아니라 **verify/fix 반복을 전제로 한 persistent mode**로 이해해야 한다.

### 4. OMC는 단순 명령어 모음이 아니라 상태를 가진 운영 체계다

`docs/ARCHITECTURE.md`, `src/hooks/`, `src/team/`, `.omc/` 상태 디렉터리 설계를 보면,
OMC는 그냥 slash command 묶음이 아니라 **작업 상태와 실행 정책을 지속적으로 다루는 시스템**에 가깝다.

### 5. OpenClaw 연동은 주변 기능이 아니라 공식 통합 포인트다

원본에 `docs/OPENCLAW-ROUTING.md`와 `src/openclaw/`가 별도로 존재한다. 즉 OpenClaw는 부록이 아니라 **실제 운영 라우팅 표면**이다.

---

## 빠른 시작: 학습자 기준 첫 성공 루프

### 1단계 — 설치 경로 이해

#### 기본 권장 경로: Claude Code plugin / marketplace

```bash
/plugin marketplace add https://github.com/Yeachan-Heo/oh-my-claudecode
/plugin install oh-my-claudecode
```

#### 보조 경로: npm package

```bash
npm i -g oh-my-claude-sisyphus@latest
```

> 헷갈리기 쉬운 포인트: 설치 명령에서 npm 이름은 `oh-my-claude-sisyphus`다.

### 2단계 — setup 실행

```bash
/setup
/omc-setup
```

### 3단계 — 가장 짧은 사용 경험 하나 만들기

```text
autopilot: build a REST API for managing tasks
```

이건 “OMC가 알아서 실행 모드를 붙여준다”는 감을 잡는 가장 짧은 진입점이다.

### 4단계 — 그다음은 Team으로 넘어가기

```bash
/team 3:executor "fix all TypeScript errors"
```

여기서부터 OMC를 **그냥 편의 명령어가 아니라 orchestration 표면**으로 보기 시작하면 된다.

---

## 핵심 표면 요약

| 표면 | 역할 | 언제 먼저 배우면 좋은가 |
|---|---|---|
| `autopilot` | 빠른 end-to-end 실행 | OMC 감을 가장 빨리 잡고 싶을 때 |
| `/team` | canonical orchestration | OMC의 중심 철학을 배우고 싶을 때 |
| `omc team` | tmux CLI workers 운영 | Codex/Gemini/Claude CLI worker 운영을 보고 싶을 때 |
| `ralph` | verify/fix 지속 루프 | 중간에 멈추면 안 되는 작업을 다룰 때 |
| `deep-interview` | 요구사항 정제 | 아직 뭘 만들어야 할지 흐릴 때 |
| `omc ask` | provider advisor 호출 | 자문 결과를 artifact로 남기고 싶을 때 |
| `/ccg` | Codex + Gemini + Claude 합성 | 다중 시각 교차 검토가 필요할 때 |
| `omc hud` | 상태 가시화 | 현재 worker / 세션 / 런타임 상황을 보고 싶을 때 |
| hooks | 자동화/후처리 확장 | 운영 흐름을 커스터마이즈하고 싶을 때 |

---

## 추천 읽기 순서

### 처음 배우는 사람

1. 이 `README.md`
2. [`01-learning-paths.md`](01-learning-paths.md)
3. [`02-glossary.md`](02-glossary.md)
4. [`sections/01-overview.md`](sections/01-overview.md)
5. 원본 `README.md`

### 구조까지 이해하고 싶은 사람

1. 원본 `docs/MIGRATION.md`
2. 원본 `docs/REFERENCE.md`
3. 원본 `docs/ARCHITECTURE.md`
4. 원본 `docs/OPENCLAW-ROUTING.md`
5. `src/team/`, `src/hooks/`, `src/openclaw/`, `src/notifications/`

---

## 원본 repo를 읽을 때 핵심 디렉터리

| 경로 | 왜 중요한가 |
|---|---|
| `agents/` | 역할별 에이전트 프롬프트 원문이 있다 |
| `skills/` | 사용자가 체감하는 workflow catalog가 있다 |
| `bridge/` | CLI/runtime 진입점이 있다 |
| `docs/` | architecture, migration, reference, routing 문서가 모여 있다 |
| `src/team/` | Team runtime의 실제 중심 구현이다 |
| `src/hooks/` | OMC 동작을 바꾸는 lifecycle/hook 계층이다 |
| `src/openclaw/` | OpenClaw 통합 로직이 있다 |
| `src/notifications/` | 알림/콜백/메시지 라우팅이 있다 |
| `src/hud/` | HUD 렌더링과 상태 표시 계층이 있다 |
| `src/features/` | notepad, verification, state-manager 같은 핵심 기능이 퍼져 있다 |

---

## 자주 하는 오해

### 오해 1. OMC는 Claude Code를 대체하는 별도 제품이다
아니다. **Claude Code 위에 얹는 운영 레이어**로 이해하는 편이 정확하다.

### 오해 2. `team`과 `omc team`은 그냥 같은 명령의 별칭이다
아니다. 관련은 깊지만, **보여주는 층위가 다르다.** `/team`은 canonical orchestration 표면, `omc team`은 tmux CLI runtime 표면이다.

### 오해 3. OMC는 Claude 전용이라 외부 모델은 주변 기능이다
아니다. 현재 구조는 Codex/Gemini 자문, CLI workers, `/ccg` 같은 표면을 통해 **멀티 모델 운영**을 명시적으로 드러낸다.

### 오해 4. hooks나 OpenClaw는 나중에 봐도 되는 부가 기능이다
입문은 뒤로 미뤄도 되지만, OMC의 정체를 이해하려면 결국 봐야 한다. OMC를 운영 체계로 만드는 핵심이 바로 이 레이어다.

---

## 다음에 무엇을 읽으면 좋은가

- **바로 학습 순서가 필요하면** → [`01-learning-paths.md`](01-learning-paths.md)
- **용어부터 헷갈리면** → [`02-glossary.md`](02-glossary.md)
- **이번 가이드가 무엇을 기준으로 재작성됐는지 보려면** → [`sections/01-overview.md`](sections/01-overview.md)
- **upstream 기준점과 최근 동기화 기록을 보려면** → [`UPSTREAM-SNAPSHOT.md`](UPSTREAM-SNAPSHOT.md), [`SYNC-LOG.md`](SYNC-LOG.md)

---

## 이 가이드의 판단

지금 기준의 OMC는 이렇게 이해하는 게 가장 덜 헷갈린다.

> **OMC는 Claude Code용 멀티 에이전트 운영 런타임이며, 현재 학습의 중심축은 Team orchestration, tmux CLI workers, hooks/state, 그리고 OpenClaw 라우팅이다.**

README만 보면 “기능이 많다”에서 끝나기 쉽다. 하지만 docs와 src를 같이 보면, 이 프로젝트의 본질은 기능 나열이 아니라 **실행을 조직하는 방식 자체**에 있다.
