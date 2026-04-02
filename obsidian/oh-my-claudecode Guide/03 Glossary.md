# 03 Glossary

[[oh-my-claudecode Guide - MOC]]

## 가장 먼저 구분할 용어

### Team
현재 OMC의 canonical orchestration surface.

### omc team
실제 tmux CLI workers를 운영하는 runtime 표면.

### Ralph
verify/fix 루프를 전제로 하는 persistent execution mode.

### hooks
실행 lifecycle에 규칙과 후처리를 주입하는 확장 포인트.

### .omc/
OMC의 상태 디렉터리. sessions, artifacts, replay/state가 모인다.

### OpenClaw integration
OMC 이벤트를 normalized signal 형태로 라우팅하는 통합 계층.

## 같이 보면 좋은 노트

- [[Concepts/Team vs omc team]]
- [[Concepts/Hooks and State]]
