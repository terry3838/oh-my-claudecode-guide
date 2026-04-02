# oh-my-claudecode 용어집

**OMC를 읽다가 자주 헷갈리는 용어를, 학습자 기준으로 다시 정리한 사전**

---

## 이 용어집을 보는 법

이 문서는 단순 번역 사전이 아니다. 각 용어마다 아래를 짧게 정리한다.

- **정의**: 이 용어가 OMC에서 무슨 뜻인지
- **왜 중요하나**: 학습자가 왜 이걸 구분해야 하는지
- **헷갈리기 쉬운 비교**: 비슷한 표면과 무엇이 다른지

---

## A

### Autopilot

**정의**
OMC의 빠른 자율 실행 표면. 사용자의 고수준 요청을 받아 end-to-end로 진행하려는 실행 모드다.

**왜 중요하나**
처음 OMC를 체험할 때 가장 부담이 적은 진입점이다.

**헷갈리기 쉬운 비교**
- `team`보다 가볍다.
- `ralph`보다 완료 집착이 덜 강하다.

**예시**
```text
autopilot: build a REST API for managing tasks
```

---

## C

### ccg

**정의**
Codex와 Gemini 관점을 받아 Claude가 결과를 합성하는 표면. 원본 README는 `/ask codex` + `/ask gemini` + Claude synthesis 패턴으로 설명한다.

**왜 중요하나**
OMC가 Claude 단독이 아니라 **교차 검토용 멀티 모델 운영**도 중시한다는 점을 보여준다.

**예시**
```text
/ccg Review this PR — architecture (Codex) and UI components (Gemini)
```

---

### Claude Code native teams

**정의**
Claude Code 자체가 제공하는 experimental teams 기능. OMC의 Team surface는 이 기능과 fallback 전략을 조합해 동작할 수 있다.

**활성화 예시**
```json
{
  "env": {
    "CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS": "1"
  }
}
```

**왜 중요하나**
OMC의 Team을 “완전히 독립된 별도 시스템”으로 오해하지 않게 해준다.

---

## D

### deep-interview

**정의**
요구사항이 모호할 때 소크라테스식 질문으로 문제를 정리하는 스킬.

**왜 중요하나**
OMC가 바로 코드를 뱉는 도구가 아니라, **무엇을 만들어야 하는지부터 정제하는 체계**라는 점을 잘 보여준다.

**예시**
```text
/deep-interview "I want to build a task management app"
```

---

### `.omc/`

**정의**
OMC의 런타임 상태 디렉터리.

**보통 들어있는 것**
- sessions
- artifacts
- state / replay 데이터
- hooks
- project-level skills

**왜 중요하나**
이 디렉터리를 보면 OMC를 단순 command pack이 아니라 **상태를 가진 운영 시스템**으로 이해하게 된다.

---

## H

### hooks

**정의**
OMC에 자동화 규칙과 후처리를 연결하는 lifecycle 확장 포인트.

**왜 중요하나**
OMC의 개성이 “프롬프트가 좋다”에서 끝나지 않고, **실행 흐름을 주입/수정한다**는 데 있다는 걸 보여준다.

**관련 표면**
- session lifecycle
- persistent mode
- team pipeline
- notifications
- todo continuation

---

### HUD

**정의**
작업 상태, worker 상태, 세션 흐름을 표시하는 시각적 상태 계층.

**왜 중요하나**
OMC의 운영자 감각을 이해하게 해준다. 단순 결과만 보는 게 아니라, **실행 중 상태를 관찰**하는 표면이다.

**예시**
```bash
omc hud
```

---

## M

### migration

**정의**
OMC의 버전 변화에 따라 권장 표면이나 폐기된 표면이 어떻게 바뀌었는지 설명하는 문서/맥락.

**왜 중요하나**
OMC는 변화 속도가 빨라서, 예전 문서와 현재 동작이 섞여 보일 수 있다. `docs/MIGRATION.md`를 안 보면 학습 축을 잘못 잡기 쉽다.

---

### marketplace / plugin install path

**정의**
Claude Code plugin 시스템을 통해 OMC를 설치하는 기본 경로.

**예시**
```bash
/plugin marketplace add https://github.com/Yeachan-Heo/oh-my-claudecode
/plugin install oh-my-claudecode
```

**왜 중요하나**
현재 문서 흐름상 가장 안전한 기본 설치 경로로 이해하는 편이 좋다.

---

## O

### oh-my-claude-sisyphus

**정의**
OMC의 npm package 이름.

**왜 중요하나**
초심자가 가장 많이 헷갈리는 지점 중 하나다.

**비교**
- 브랜드/리포 이름: `oh-my-claudecode`
- npm package 이름: `oh-my-claude-sisyphus`

**예시**
```bash
npm i -g oh-my-claude-sisyphus@latest
```

---

### OMC

**정의**
oh-my-claudecode의 약칭.

**학습자용 한 줄 설명**
Claude Code 위에 팀 실행, 검증 루프, 상태 저장, 외부 라우팅을 덧씌우는 멀티 에이전트 운영 런타임.

---

### `omc ask`

**정의**
Claude, Codex, Gemini 같은 provider CLI를 자문용으로 호출하고 결과를 artifact로 남기는 표면.

**왜 중요하나**
구현과 별도로 **advisor 결과를 보존하고 비교**하는 학습 흐름을 지원한다.

**예시**
```bash
omc ask claude "review this migration plan"
omc ask codex --prompt "identify architecture risks"
omc ask gemini --prompt "propose UI polish ideas"
```

---

### `omc team`

**정의**
tmux 기반 CLI workers를 운영하는 OMC의 runtime 표면.

**왜 중요하나**
현재 OMC가 provider abstraction보다 **실제 worker 운영** 쪽으로 얼마나 무게중심이 이동했는지 보여준다.

**헷갈리기 쉬운 비교**
- `/team`: canonical orchestration surface
- `omc team`: tmux CLI runtime surface

**예시**
```bash
omc team 2:codex "review auth module for security issues"
```

---

### OpenClaw integration

**정의**
OMC 이벤트를 OpenClaw 쪽으로 라우팅하는 공식 통합 계층.

**왜 중요하나**
원본에 문서와 소스 디렉터리가 따로 존재할 정도로 비중이 있다. 단순 알림이 아니라 **정규화된 signal contract**를 가진 운영 통합 포인트다.

**관련 근거**
- `docs/OPENCLAW-ROUTING.md`
- `src/openclaw/`

---

### orchestration

**정의**
여러 worker나 단계를 단순 병렬 실행하는 게 아니라, **계획-실행-검증 흐름을 조율하는 것**.

**왜 중요하나**
이 단어를 정확히 이해해야 `team`의 본질을 놓치지 않는다.

---

## P

### pipeline

**정의**
작업을 의미 있는 순서로 분해해 진행하는 단계 흐름.

**OMC에서의 대표 예시**
```text
team-plan → team-prd → team-exec → team-verify → team-fix
```

**왜 중요하나**
OMC는 “좋은 프롬프트 한 번”보다 **단계적 실행 구조**를 더 중시한다.

---

### plugin install

**정의**
Claude Code plugin 시스템으로 OMC를 설치하는 방식.

**왜 중요하나**
현재 reference 계열 문서와 가장 잘 맞는 기본 설치 감각이다.

---

### prompts / agents

**정의**
역할별 행동 템플릿과 에이전트 정의.

**예시 역할**
- planner
- executor
- architect
- debugger
- verifier
- critic

**왜 중요하나**
OMC가 문제를 다양한 역할로 나눠 보게 만드는 기반이다.

**헷갈리기 쉬운 비교**
- agents: 역할 그 자체
- skills: workflow 단위 행동 주입

---

## R

### Ralph

**정의**
검증이 끝날 때까지 멈추지 않으려는 persistent execution mode.

**왜 중요하나**
OMC가 “적당히 한 번 시도해보는 도구”가 아니라, **완료를 더 집요하게 밀어붙이는 운영 모드**를 가진다는 점을 보여준다.

**예시**
```text
ralph: refactor auth and make sure it is fully verified
```

---

### runtime

**정의**
실행을 실제로 굴리는 계층. OMC에서는 hooks, workers, state, notifications, routing이 함께 얽힌 실전 동작 층을 뜻하는 경우가 많다.

**왜 중요하나**
OMC를 프롬프트 모음과 구분해 주는 단어다.

---

## S

### skills

**정의**
작업 방식을 바꾸는 workflow 단위 행동 묶음.

**예시**
- `autopilot`
- `team`
- `ralph`
- `deep-interview`
- `configure-notifications`

**왜 중요하나**
OMC의 사용자 체감 기능 대부분은 skill 단위로 드러난다.

**헷갈리기 쉬운 비교**
- skills는 **행동 패턴**
- agents는 **역할 단위 실행자**

---

### state

**정의**
현재 세션, artifacts, replay, 진행 정보처럼 OMC가 작업 흐름을 이어가기 위해 보존하는 정보.

**왜 중요하나**
상태가 있어야 verify/fix 루프, artifact 축적, session 기반 운영이 가능하다.

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

---

### tmux CLI workers

**정의**
`omc team`이 띄우는 실제 `claude`, `codex`, `gemini` CLI worker pane들.

**왜 중요하나**
현재 OMC의 실전 운영 감각을 가장 잘 보여주는 표면이다.

**관련 예시**
```bash
omc team 2:gemini "redesign UI components for accessibility"
```

---

## V

### verify / fix loop

**정의**
구현 후 검증하고, 문제가 남아 있으면 수정하고, 다시 확인하는 반복 구조.

**왜 중요하나**
OMC를 단순 생성 도구가 아니라 **완료 품질까지 챙기는 실행 체계**로 만든다.

---

## 이 용어집의 결론

OMC를 읽을 때 가장 먼저 구분해야 하는 축은 이것이다.

- **agent vs skill**
- **`/team` vs `omc team`**
- **autopilot vs ralph**
- **command surface vs runtime/state**

이 네 축만 분명해져도 README와 docs를 읽을 때 체감 난도가 크게 내려간다.
