# oh-my-claudecode 학습 경로

OMC는 지금 **표면을 구분해서 배우는 것**이 제일 중요해요.

1. plugin vs npm CLI
2. `/team` vs `omc team`
3. Team pipeline vs hooks/state/HUD

## 트랙 1. 처음 쓰는 사용자

목표:
- plugin 설치와 첫 in-session 실행을 경험해요
- Team이 canonical surface라는 점을 이해해요

읽는 순서:
1. `README.md`
2. `sections/01-overview.md`
3. `02-glossary.md`

실습:
```bash
/plugin install oh-my-claudecode
/setup
/omc-setup
```

그 다음:
```text
/autopilot "build a REST API for managing tasks"
/team 3:executor "fix all TypeScript errors"
```

## 트랙 2. 운영자

목표:
- plugin-dir 기반 운영에서 중복 설치를 피하고, tmux worker runtime을 구분해요

읽는 순서:
1. `sections/02-team-runtime-and-worker-model.md`
2. `sections/03-hooks-openclaw-and-observability.md`
3. upstream `README.md`의 plugin-dir / CLI / Team 구간

핵심 확인:
- `--plugin-dir-mode`
- `OMC_PLUGIN_ROOT`
- `/team` vs `omc team`

## 트랙 3. 통합 담당자

목표:
- hooks, notifications, OpenClaw routing을 운영 표면으로 읽어요

읽는 순서:
1. `sections/03-hooks-openclaw-and-observability.md`
2. upstream `docs/OPENCLAW-ROUTING.md` 또는 관련 docs
3. `02-glossary.md`

성공 기준:
- OMC를 plugin만이 아니라 runtime/system으로 설명할 수 있어요
