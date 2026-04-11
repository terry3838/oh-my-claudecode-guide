# oh-my-claudecode 개요

## repo 역할

- repo: `oh-my-claudecode`
- source: `https://github.com/Yeachan-Heo/oh-my-claudecode.git`
- version basis: `4.11.4`
- latest synced commit: `7b4a9e0435b7`

## 왜 frontdoor를 다시 썼나

기존 문서도 repo breadth는 잘 보여줬지만,
최근 upstream docs가 더 선명하게 강조하는 세 가지를 frontdoor에서 더 앞쪽에 놓을 필요가 있었어요.

1. plugin 설치와 npm CLI 설치가 공존한다는 점
2. `/team`과 `omc team`이 다른 표면이라는 점
3. `--plugin-dir-mode`와 Team canonical flow가 현재 운영 계약이라는 점

## 지금 기준의 핵심 메시지

- OMC는 Claude Code runtime이에요
- Team이 현재 canonical orchestration surface예요
- plugin-only로 보면 반쪽 이해가 돼요
- hooks/state/HUD/OpenClaw routing까지 함께 봐야 현재 구조가 보여요

## 학습자가 먼저 볼 것

- `README.md`
- `01-learning-paths.md`
- `sections/02-team-runtime-and-worker-model.md`
- `sections/03-hooks-openclaw-and-observability.md`

## 다음 행동

처음이면 `/team`과 `omc team` 차이부터 잡으세요.
운영자면 plugin-dir mode와 hooks/OpenClaw 표면을 같이 보세요.
