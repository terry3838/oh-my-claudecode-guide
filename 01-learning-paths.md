# oh-my-claudecode 학습 경로

**입문 → orchestration 이해 → 운영 관점 → 확장/통합** 순서로 OMC를 배우기 위한 읽기 경로

---

## 왜 이 순서가 필요한가

OMC는 표면이 많다. `autopilot`, `team`, `ralph`, `omc team`, hooks, HUD, OpenClaw, skills, agents가 한꺼번에 보이기 때문에, 처음부터 전체를 펼쳐 보면 오히려 더 헷갈린다.

그래서 이 가이드는 기능 나열 대신 **학습 순서**를 먼저 정한다.

이 순서의 원칙은 세 가지다.

1. **먼저 frontdoor를 이해한다**
   - OMC가 무엇인지, 무엇이 중심 표면인지부터 잡는다.
2. **그다음 orchestration을 배운다**
   - `team`과 `ralph`를 모르면 OMC를 단순 자동화 도구로 오해하기 쉽다.
3. **마지막에 운영/통합으로 내려간다**
   - hooks, tmux, OpenClaw는 중요하지만, 정체를 모른 채 보면 세부 구현으로만 보인다.

---

## 전체 로드맵

| 단계 | 핵심 질문 | 목표 |
|---|---|---|
| 1단계. 입문 | OMC는 정확히 뭐지? | 표면과 버전 기준을 잡는다 |
| 2단계. 중심 사용법 | 왜 `team`이 핵심이지? | canonical orchestration을 이해한다 |
| 3단계. 운영 관점 | `omc team`, HUD, `.omc/`는 왜 필요하지? | 런타임 운영 구조를 읽는다 |
| 4단계. 확장/통합 | hooks와 OpenClaw는 어디에 붙지? | 시스템 확장 포인트를 이해한다 |
| 5단계. 기여/분석 | 실제 구현은 어디를 읽어야 하지? | src 구조를 기반으로 source reading이 가능해진다 |

### Mermaid 로 보는 학습 순서 맵

```mermaid
flowchart LR
    A[1. 입문] --> B[2. Team 중심 사용법]
    B --> C[3. 운영 관점]
    C --> D[4. 확장/통합]
    D --> E[5. Source Reading]
    A --> A1[README]
    A --> A2[package naming]
    B --> B1[/team]
    B --> B2[ralph]
    C --> C1[omc team]
    C --> C2[HUD/.omc]
    D --> D1[hooks]
    D --> D2[OpenClaw]
    E --> E1[src/team]
    E --> E2[src/hooks]
    E --> E3[src/openclaw]
```

이 맵은 “무슨 기능이 많다”보다 **무슨 순서로 이해해야 덜 헷갈리는가**를 보여준다.

---

## 1단계 — 입문: OMC를 한 문장으로 설명할 수 있게 만들기

### 목표

- OMC를 **Claude Code용 운영 런타임**으로 설명할 수 있다.
- `oh-my-claudecode`와 `oh-my-claude-sisyphus`의 차이를 안다.
- Team이 현재 중심 표면이라는 것을 안다.
- plugin 경로와 npm 경로의 차이를 안다.

### 먼저 읽을 것

1. 이 가이드의 `README.md`
2. 원본 `README.md`
3. 원본 `package.json`
4. 필요 시 원본 `docs/MIGRATION.md`의 관련 구간

### 이 단계에서 꼭 잡아야 할 사실

#### A. 브랜딩 이름과 npm 패키지 이름이 다르다

```text
repo / plugin / command branding: oh-my-claudecode
npm package: oh-my-claude-sisyphus
```

#### B. Team이 지금 기준의 canonical surface다

입문자가 예전 글만 보고 `swarm`부터 배우면 이미 구조를 잘못 잡는다.

#### C. 설치보다 더 중요한 건 setup 이후의 실행 철학이다

설치가 끝이 아니라, OMC가 어떤 식으로 **작업을 분해하고 지속시키는지**를 이해해야 한다.

### 첫 실습 예시

```text
autopilot: build a REST API for managing tasks
```

이 예시는 “OMC가 자연어 요청을 실행 흐름으로 바꾸는 느낌”을 보는 데 적합하다.

### 체크리스트

- [ ] OMC를 “Claude Code용 멀티 에이전트 운영 런타임”으로 설명할 수 있다.
- [ ] plugin 설치 경로와 npm 설치 경로의 차이를 안다.
- [ ] package naming 차이를 안다.
- [ ] Team이 현재 중심 표면이라는 것을 안다.

---

## 2단계 — 중심 사용법: Team / Ralph / Autopilot의 차이 이해하기

### 목표

- `autopilot`, `team`, `ralph`를 용도별로 구분할 수 있다.
- Team pipeline을 단계별로 설명할 수 있다.
- `/team`과 `omc team`을 같은 것으로 오해하지 않는다.

### 읽을 것

1. 원본 `README.md`의 Team / tmux workers 구간
2. 원본 `docs/MIGRATION.md`
3. 이 가이드의 `02-glossary.md`

### 핵심 개념

#### 1. Autopilot
- 빠른 end-to-end 실행 감을 잡는 표면
- 처음 접할 때 가장 부담이 적다

#### 2. Team
- current canonical orchestration surface
- 핵심은 staged pipeline

```text
team-plan → team-prd → team-exec → team-verify → team-fix (loop)
```

#### 3. Ralph
- verify/fix 지속 루프를 전제로 한 persistence mode
- “중간쯤 했으니 끝”을 덜 허용한다

### 꼭 구분할 것: `/team` vs `omc team`

| 표면 | 보는 층위 | 의미 |
|---|---|---|
| `/team` | 사용자/학습자 표면 | canonical orchestration |
| `omc team` | 운영자/런타임 표면 | tmux CLI workers 운영 |

### 추천 실습

#### 실습 1 — canonical surface 보기

```bash
/team 3:executor "fix all TypeScript errors"
```

#### 실습 2 — 완료 집착 모드 보기

```text
ralph: refactor auth and make sure it is fully verified
```

#### 실습 3 — 요구 정제 먼저 하기

```text
/deep-interview "I want to build a task management app"
```

### 체크리스트

- [ ] `autopilot`과 `team`의 차이를 설명할 수 있다.
- [ ] `team`과 `ralph`의 차이를 설명할 수 있다.
- [ ] Team pipeline 각 단계를 설명할 수 있다.
- [ ] `/team`과 `omc team`을 구분할 수 있다.

---

## 3단계 — 운영 관점: tmux workers, HUD, artifacts, state 읽기

### 목표

- `omc team N:codex|gemini|claude`가 무엇을 의미하는지 안다.
- worker runtime이 tmux 의존성이 크다는 것을 이해한다.
- `.omc/`와 artifacts를 통해 OMC를 상태 기반 시스템으로 볼 수 있다.

### 읽을 것

1. 원본 `README.md`의 tmux CLI workers 구간
2. 원본 `docs/REFERENCE.md`의 `omc team`, `omc ask`, configuration 구간
3. 원본 `docs/MIGRATION.md`의 Team MCP runtime deprecation 구간

### 핵심 포인트

#### 1. `omc team`은 실제 CLI worker pane을 다룬다

```bash
omc team 2:codex "review auth module for security issues"
omc team 2:gemini "redesign UI components for accessibility"
omc team 1:claude "implement the payment flow"
```

#### 2. provider별 감각 차이

| worker | 강한 영역 |
|---|---|
| `claude` | 일반 구현, 디버깅, 텍스트 중심 작업 |
| `codex` | 코드 리뷰, 구조 점검, 보안/아키텍처 관점 |
| `gemini` | UI/UX, 대형 컨텍스트 문서, 시각/설계 관점 |

#### 3. `omc ask`와 `/ccg`

- `omc ask`: 특정 provider의 의견을 artifact로 남기는 자문 표면
- `/ccg`: Codex + Gemini 의견을 받은 뒤 Claude가 합성하는 교차 검토 표면

#### 4. `.omc/`를 봐야 OMC가 보인다

보통 아래를 먼저 보면 좋다.

- `.omc/artifacts/ask/`
- `.omc/sessions/`
- `.omc/state/`
- `.omc/hooks/`

### 체크리스트

- [ ] `omc team 2:codex`가 의미하는 바를 안다.
- [ ] tmux가 왜 중요한지 안다.
- [ ] `omc ask`와 `/ccg` 차이를 설명할 수 있다.
- [ ] `.omc/`를 왜 봐야 하는지 안다.

---

## 4단계 — 확장/통합: hooks와 OpenClaw 읽기

### 목표

- OMC가 왜 “운영 체계”로 불리는지 이해한다.
- hooks와 notifications, OpenClaw routing의 연결을 설명할 수 있다.

### 읽을 것

1. 원본 `docs/ARCHITECTURE.md`
2. 원본 `docs/OPENCLAW-ROUTING.md`
3. 원본 `docs/REFERENCE.md`의 hooks 관련 구간
4. 소스: `src/hooks/`, `src/notifications/`, `src/openclaw/`

### 먼저 이해할 구조

#### hooks
- lifecycle 이벤트에 행동을 연결하는 계층
- setup, persistent-mode, team-pipeline, todo continuation 같은 운영 규칙이 이 층에 깔린다

#### notifications
- 상태 변화나 결과를 외부 채널/콜백으로 보내는 계층

#### OpenClaw
- OMC 이벤트를 정규화된 payload로 내보내는 공식 bridge
- raw hook event보다 `signal` 중심 라우팅이 중요해진다

### 이 단계에서 꼭 남길 이해

> OMC는 단순히 “좋은 프롬프트 모음”이 아니라, **이벤트를 감지하고, 적절한 행동을 주입하고, 상태를 유지하고, 바깥 시스템으로 신호를 보내는 런타임**이다.

### 체크리스트

- [ ] hooks의 역할을 설명할 수 있다.
- [ ] notifications 계층이 왜 필요한지 안다.
- [ ] OpenClaw routing 문서가 무엇을 정의하는지 안다.
- [ ] OMC를 상태 기반 운영 시스템으로 볼 수 있다.

---

## 5단계 — source reading: 어디부터 읽어야 덜 헤매는가

### 목표

- 원본 repo 구조를 학습 목적에 맞게 읽을 수 있다.
- docs와 src의 연결 지점을 파악한다.

### 추천 읽기 순서

#### A. 문서 우선
1. `README.md`
2. `docs/MIGRATION.md`
3. `docs/REFERENCE.md`
4. `docs/ARCHITECTURE.md`
5. `docs/OPENCLAW-ROUTING.md`

#### B. 구조 확인
1. `agents/`
2. `skills/`
3. `bridge/`
4. `src/team/`
5. `src/hooks/`
6. `src/openclaw/`
7. `src/notifications/`
8. `src/hud/`

#### C. 구현 디테일 확장
- `src/features/`
- `src/providers/`
- `src/verification/`
- `src/planning/`

### source reading 질문 예시

- Team pipeline은 문서 설명과 코드 책임이 어떻게 대응되는가?
- `omc team` 관련 CLI runtime은 어디서 시작되는가?
- OpenClaw signal payload는 어디서 구성되는가?
- persistence 관련 동작은 hooks 계층에서 어떻게 주입되는가?

---

## 추천 학습 루프

### 가장 현실적인 3회독 방식

#### 1회독 — 표면 익히기
- README 위주
- `autopilot`, `team`, `ralph`, `omc team` 이름과 역할만 잡기

#### 2회독 — 운영 개념 잡기
- MIGRATION + REFERENCE + `.omc/` 구조
- tmux workers, artifact, state, deprecation 흐름 이해하기

#### 3회독 — 시스템 이해하기
- ARCHITECTURE + OPENCLAW-ROUTING + `src/hooks/`, `src/team/`
- 실제 책임 분리를 확인하기

---

## 이 학습 경로의 결론

OMC를 가장 덜 헷갈리게 배우는 순서는 이것이다.

> **autopilot으로 감을 잡고 → Team으로 중심 철학을 배우고 → `omc team`과 `.omc/`로 운영 구조를 보고 → hooks / OpenClaw로 시스템의 본체를 이해한다.**

이 순서를 따르면 기능 목록에 압도되지 않고, OMC를 **실행을 조직하는 시스템**으로 이해할 수 있다.
