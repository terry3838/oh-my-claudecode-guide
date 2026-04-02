# oh-my-claudecode 용어집

**OMC를 읽을 때 자주 헷갈리는 용어를, 문서/구현/운영 관점까지 붙여 다시 정리한 사전**

---

## 이 용어집의 목적

OMC에서 초심자가 가장 자주 꼬이는 지점은 단어 자체보다 **단어가 가리키는 층위**다.

예를 들어:
- `team`은 orchestration surface고
- `omc team`은 runtime surface고
- `agent`는 역할이고
- `skill`은 행동 주입이고
- `hook`은 lifecycle injection이고
- `state`는 실행 흔적/연속성 기반이다.

이 문서는 각 용어마다 아래를 짧게 정리한다.

- **정의**: 이 용어가 OMC에서 무슨 뜻인지
- **왜 중요하나**: 왜 이걸 구분해야 하는지
- **헷갈리기 쉬운 비교**: 비슷한 용어와 무엇이 다른지
- **근거 surface**: 주로 어디서 확인되는지

---

## 가장 먼저 구분해야 하는 6축

1. **agent vs skill**
2. **`/team` vs `omc team`**
3. **autopilot vs ralph**
4. **command surface vs runtime surface**
5. **hook event vs OpenClaw signal**
6. **README frontdoor vs current repo reality**

이 여섯 축이 안 잡히면 OMC 문서는 계속 비슷해 보이는데, 실제로는 다른 층위를 설명하고 있어서 혼란이 커진다.

---

## A

### agent

**정의**
특정 역할을 맡는 실행자. 예: `planner`, `executor`, `architect`, `critic`, `verifier`.

**왜 중요하나**
OMC는 문제를 한 덩어리로 처리하기보다 **역할 분리**로 푸는 성향이 강하다. agent는 그 역할 분리의 기본 단위다.

**헷갈리기 쉬운 비교**
- agent = 역할 단위 실행자
- skill = 행동 방식을 주입하는 패턴

**근거 surface**
- `agents/`
- `docs/ARCHITECTURE.md`
- 원본 README의 agent 설명

---

### Agent Observatory

**정의**
실행 중인 agent들의 상태, 비용, 병목, 효율을 보여주는 관측 표면.

**왜 중요하나**
OMC가 단순 실행뿐 아니라 **실행 관측**까지 공식적으로 다루는 시스템이라는 걸 보여준다.

**근거 surface**
- `docs/PERFORMANCE-MONITORING.md`
- HUD / observatory 관련 구현

---

### autopilot

**정의**
고수준 자연어 요청을 받아 end-to-end 실행으로 밀어주는 빠른 entry surface.

**왜 중요하나**
OMC를 가장 빨리 체험하게 해주는 진입점이다.

**헷갈리기 쉬운 비교**
- `team`보다 덜 구조적일 수 있다
- `ralph`보다 완료 집착이 약하다

**예시**
```text
autopilot: build a REST API for managing tasks
```

**근거 surface**
- 원본 README
- `docs/FEATURES.md`

---

## C

### `/ccg`

**정의**
Codex와 Gemini 관점을 받은 뒤 Claude가 결과를 합성하는 tri-model advisor surface.

**왜 중요하나**
OMC가 Claude 단독 도구가 아니라 **멀티 모델 cross-check**를 적극적으로 활용한다는 걸 보여준다.

**헷갈리기 쉬운 비교**
- `/ccg`는 합성 workflow
- `omc ask`는 provider별 advisor 호출

**근거 surface**
- 원본 README
- `docs/REFERENCE.md`

---

### Claude Code native teams

**정의**
Claude Code 자체가 제공하는 experimental teams 기능.

**왜 중요하나**
OMC의 Team을 완전히 독립된 외부 시스템으로 오해하지 않게 해준다. OMC는 이 표면과 fallback/runtime 전략을 같이 다룬다.

**근거 surface**
- 원본 README Team 구간

---

### command surface

**정의**
사용자가 직접 호출하거나 체감하는 명령/스킬/키워드 표면.

**예시**
- `autopilot`
- `/team`
- `ralph`
- `/ccg`
- `/deep-interview`

**왜 중요하나**
이 층만 보면 OMC가 “편한 명령 모음”처럼 보이기 쉽다.

**헷갈리기 쉬운 비교**
- command surface = 사용자 진입점
- runtime surface = 실제 실행을 굴리는 층

---

## D

### deep-interview

**정의**
모호한 요구사항을 소크라테스식 질문으로 정리하는 스킬.

**왜 중요하나**
OMC가 무조건 코딩부터 하는 게 아니라, **문제 정의를 먼저 다듬는 체계**라는 점을 보여준다.

**예시**
```text
/deep-interview "I want to build a task management app"
```

**근거 surface**
- 원본 README
- skills 계층

---

### drift

**정의**
문서, 구현, 버전 설명 사이의 기준선 차이.

**왜 중요하나**
OMC는 빠르게 진화하는 repo라서 README, migration, architecture, reference 문서가 완전히 같은 관점으로 쓰이지 않는다.

**예시**
- `32 specialized agents` vs `19 specialized agents`
- `31 skills` vs `32 skills` vs `37 core skills`
- plugin+npm 설치 설명 vs plugin-only 강조

**근거 surface**
- 원본 `README.md`
- `docs/MIGRATION.md`
- `docs/ARCHITECTURE.md`
- `docs/REFERENCE.md`

---

### `.omc/`

**정의**
OMC의 상태 저장 디렉터리.

**자주 보는 하위 구조**
- `artifacts/`
- `sessions/`
- `state/`
- `notepads/`
- project-level skills/hooks 관련 데이터

**왜 중요하나**
이 경로를 보면 OMC가 단순 명령 세트가 아니라 **상태를 가진 운영 시스템**이라는 점이 선명해진다.

**근거 surface**
- `docs/REFERENCE.md`
- `docs/PERFORMANCE-MONITORING.md`

---

## H

### hook / hooks

**정의**
lifecycle 이벤트에 행동을 연결하는 확장 계층.

**왜 중요하나**
OMC가 프롬프트 모음과 다른 가장 큰 이유 중 하나다. hooks를 통해 persistent mode, continuation, notifications, routing 같은 운영 행동이 살아난다.

**헷갈리기 쉬운 비교**
- hook event = 원시 이벤트
- OpenClaw signal = 라우팅 친화적으로 정규화된 이벤트 표현

**근거 surface**
- `docs/ARCHITECTURE.md`
- `docs/REFERENCE.md`
- `src/hooks/`

---

### HUD

**정의**
현재 agent, todo, mode, context, analytics 같은 런타임 정보를 시각적으로 보여주는 관측 표면.

**왜 중요하나**
OMC를 “실행 결과만 보는 도구”가 아니라 **실행 중 상태를 관찰하는 도구**로 이해하게 해준다.

**근거 surface**
- 원본 README
- `docs/PERFORMANCE-MONITORING.md`
- `src/hud/`

---

## I

### integration surface

**정의**
OMC가 외부 시스템과 연결되는 층.

**대표 예시**
- notifications
- OpenClaw bridge
- callback/webhook

**왜 중요하나**
OMC가 로컬 실행 도구를 넘어서 **운영 자동화 시스템**으로 확장되는 지점을 보여준다.

---

## M

### migration

**정의**
버전 변화에 따라 권장 표면과 폐기 표면이 어떻게 바뀌었는지 설명하는 문서/맥락.

**왜 중요하나**
현재 표면을 정확히 이해하려면, deprecated surface를 알아야 하기 때문이다.

**헷갈리기 쉬운 비교**
- README는 현재 frontdoor 메시지
- MIGRATION은 과거→현재 이동 경로

**근거 surface**
- `docs/MIGRATION.md`

---

### mission / missions

**정의**
repo 안에서 작업 단위와 그 흔적을 다루는 축.

**왜 중요하나**
OMC가 단순 샘플 repo가 아니라, 실제 작업과 운영 결과를 저장/추적하는 성격을 갖고 있음을 보여준다.

**근거 surface**
- `missions/`
- HUD mission board 관련 코드

---

## N

### notepad wisdom

**정의**
plan 단위로 learnings / decisions / issues / problems를 기록하는 지식 캡처 체계.

**왜 중요하나**
OMC가 한 번 실행하고 잊는 게 아니라, **작업 중 나온 지식을 누적하는 운영 런타임**이라는 점을 보여준다.

**근거 surface**
- `docs/FEATURES.md`
- `.omc/notepads/`
- 관련 구현

---

## O

### oh-my-claude-sisyphus

**정의**
OMC의 npm package 이름.

**왜 중요하나**
초심자가 가장 자주 헷갈리는 이름이다.

**비교**
- 브랜드/리포/플러그인: `oh-my-claudecode`
- npm package: `oh-my-claude-sisyphus`

**근거 surface**
- 원본 README
- `package.json`

---

### OMC

**정의**
oh-my-claudecode의 약칭.

**학습자용 한 줄 정의**
Claude Code 위에 orchestration, runtime workers, 상태 관리, 관측, 외부 라우팅을 얹는 운영 런타임.

---

### `omc ask`

**정의**
provider CLI를 advisor로 호출하고 결과를 artifact로 남기는 표면.

**왜 중요하나**
실행과 별개로 **provider별 관점 수집**을 가능하게 한다.

**헷갈리기 쉬운 비교**
- `omc ask` = provider 자문 단위
- `/ccg` = 여러 자문 결과를 종합하는 workflow

**예시**
```bash
omc ask claude "review this migration plan"
omc ask codex --prompt "identify architecture risks"
omc ask gemini --prompt "propose UX polish ideas"
```

**근거 surface**
- 원본 README
- `docs/REFERENCE.md`

---

### `omc team`

**정의**
tmux 기반 CLI workers를 운영하는 runtime surface.

**왜 중요하나**
최신 OMC가 provider abstraction보다 **실제 CLI worker 운영** 쪽으로 많이 기울었음을 보여준다.

**헷갈리기 쉬운 비교**
- `/team` = canonical orchestration surface
- `omc team` = tmux CLI runtime surface

**예시**
```bash
omc team 2:codex "review auth module for security issues"
```

**근거 surface**
- 원본 README
- `docs/MIGRATION.md`
- `docs/REFERENCE.md`
- `src/team/`

---

### OpenClaw integration

**정의**
OMC 이벤트를 OpenClaw 쪽으로 라우팅하는 공식 통합 계층.

**왜 중요하나**
이건 단순 알림이 아니라 **정규화된 signal contract**를 가진 운영 integration surface다.

**헷갈리기 쉬운 비교**
- hook event = 원시 이벤트
- OpenClaw signal = downstream routing용 normalized event

**근거 surface**
- `docs/OPENCLAW-ROUTING.md`
- `src/openclaw/`

---

### orchestration

**정의**
여러 역할/단계를 병렬 또는 순차로 조율하면서, 계획-실행-검증 구조를 유지하는 것.

**왜 중요하나**
이 단어를 정확히 이해해야 Team의 본질을 놓치지 않는다.

---

### observability

**정의**
실행 중 상태를 관찰하고, 병목/비용/진행을 이해하는 능력과 도구층.

**왜 중요하나**
OMC는 결과만 뱉는 도구가 아니라, **운영 가시성**을 제공하는 시스템이다.

**근거 surface**
- `docs/PERFORMANCE-MONITORING.md`
- `src/hud/`
- replay/session summary 구조

---

## P

### performance monitoring

**정의**
agent observatory, session replay, session-end summary, HUD 등을 통해 실행 품질과 병목을 추적하는 운영 표면.

**왜 중요하나**
퍼블릭 repo 기준으로 OMC의 성격을 더 진하게 보여주는 축이다. 단순히 실행하는 게 아니라 **관찰하고 최적화**하려고 만든 시스템이라는 뜻이다.

**근거 surface**
- `docs/PERFORMANCE-MONITORING.md`
- HUD / replay 관련 구현

---

### pipeline

**정의**
작업을 의미 있는 순서로 분해한 단계 흐름.

**대표 예시**
```text
team-plan → team-prd → team-exec → team-verify → team-fix
```

**왜 중요하나**
OMC는 한 번의 좋은 프롬프트보다 **단계적 실행 구조**를 중시한다.

---

### plugin install path

**정의**
Claude Code plugin 시스템을 통해 OMC를 설치하는 경로.

**왜 중요하나**
현재 reference 문서에서는 이 경로를 가장 강하게 지원/권장한다.

**근거 surface**
- 원본 README
- `docs/REFERENCE.md`

---

### provider advisor

**정의**
Claude, Codex, Gemini 같은 provider를 자문용으로 호출하는 방식.

**왜 중요하나**
OMC가 단일 모델 체험을 넘어 **cross-check / review / synthesis** 워크플로를 갖고 있음을 보여준다.

---

## R

### Ralph

**정의**
검증이 끝날 때까지 멈추지 않으려는 persistent execution mode.

**왜 중요하나**
OMC가 “대충 한 번 시도해보기”보다 **완료 보증 성향**을 가진다는 걸 드러낸다.

**예시**
```text
ralph: refactor auth and make sure it is fully verified
```

**헷갈리기 쉬운 비교**
- autopilot = 빠른 자율 실행
- ralph = verify/fix 보증 레이어가 더 강함

---

### replay

**정의**
agent/tool lifecycle 이벤트를 JSONL 등으로 남겨 나중에 다시 분석할 수 있게 하는 기록 표면.

**왜 중요하나**
실행을 단발성 결과가 아니라 **재구성 가능한 timeline**으로 다룰 수 있게 해준다.

**근거 surface**
- `docs/PERFORMANCE-MONITORING.md`
- `.omc/state/agent-replay-*.jsonl`

---

### runtime surface

**정의**
실제 worker, state, notifications, replay, hooks 같은 실행 계층.

**왜 중요하나**
OMC를 command pack과 구분해 주는 핵심 단어다.

**헷갈리기 쉬운 비교**
- command surface = 사용자가 호출하는 층
- runtime surface = 시스템이 실제로 굴러가는 층

---

## S

### session summary

**정의**
세션 종료 시 남는 요약 정보와 artifact.

**왜 중요하나**
운영자가 실행 후 결과를 다시 읽고 평가할 수 있게 만든다.

**근거 surface**
- `docs/PERFORMANCE-MONITORING.md`
- `.omc/sessions/*.json`

---

### signal

**정의**
OpenClaw routing에서 사용하는 normalized event object.

**핵심 필드 예시**
- `kind`
- `name`
- `phase`
- `routeKey`
- `priority`

**왜 중요하나**
새 통합은 raw event보다 **signal 중심**으로 이해해야 덜 헷갈린다.

**근거 surface**
- `docs/OPENCLAW-ROUTING.md`
- `src/openclaw/signal.ts`

---

### skill

**정의**
에이전트를 교체하는 것이 아니라, orchestrator의 행동 방식을 바꾸는 주입 레이어.

**왜 중요하나**
OMC의 사용자 체감 기능 대부분은 skill 단위로 드러난다.

**헷갈리기 쉬운 비교**
- skill = 행동 패턴
- agent = 역할 단위 실행자

**근거 surface**
- `skills/`
- `docs/ARCHITECTURE.md`

---

### state

**정의**
세션, artifacts, replay, notepad, 진행 정보처럼 OMC가 흐름을 이어가기 위해 보존하는 정보.

**왜 중요하나**
state가 있어야 verify/fix loop, replay, session summary, runtime continuity가 가능하다.

---

## T

### Team

**정의**
현재 OMC의 canonical orchestration surface.

**왜 중요하나**
지금 OMC를 배울 때 가장 먼저 중심에 놓아야 하는 개념이다.

**핵심 단계**
```text
team-plan → team-prd → team-exec → team-verify → team-fix
```

**헷갈리기 쉬운 비교**
- 단순 fan-out이 아니다
- orchestration + verification 구조다

**근거 surface**
- 원본 README
- `docs/MIGRATION.md`

---

### tmux CLI workers

**정의**
`omc team`이 띄우는 실제 `claude`, `codex`, `gemini` CLI worker pane들.

**왜 중요하나**
최신 OMC의 실전 운영 감각을 가장 잘 보여주는 표면이다.

**근거 surface**
- 원본 README
- `docs/REFERENCE.md`
- `src/team/`

---

## V

### verify / fix loop

**정의**
구현 → 검증 → 수정 → 재검증의 반복 구조.

**왜 중요하나**
OMC를 단순 생성 도구가 아니라 **완료 품질까지 챙기는 시스템**으로 만든다.

---

## 이 용어집의 결론

OMC를 읽을 때 가장 먼저 고정해야 하는 건 개별 기능이 아니라 **층위 구분**이다.

- 역할인가? → agent
- 행동 주입인가? → skill
- 사용자 표면인가? → command surface
- 실제 실행 계층인가? → runtime surface
- raw 이벤트인가? → hook event
- 통합용 정규화 계약인가? → OpenClaw signal

이 구분이 서면 README, docs, src를 읽을 때 훨씬 덜 헷갈린다.
