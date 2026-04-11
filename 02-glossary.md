# oh-my-claudecode 용어집

## `/team`

Claude Code 세션 안에서 쓰는 canonical Team orchestration surface예요.
공유 task lifecycle과 staged pipeline을 이해할 때 기준점이 돼요.

## `omc team`

터미널에서 tmux 기반 real worker를 띄우는 CLI runtime surface예요.
`/team`과 연결되지만 같은 층위는 아니에요.

## `--plugin-dir-mode`

plugin-dir로 OMC를 실행할 때 plugin이 이미 제공하는 skills/agents를 setup이 다시 중복 설치하지 않게 하는 운영 플래그예요.

## `OMC_PLUGIN_ROOT`

Claude를 직접 `--plugin-dir`로 띄울 때 HUD bundle과 plugin loader가 같은 checkout을 가리키도록 맞춰 주는 환경 변수예요.

## Team canonical surface

현재 OMC에서 가장 중심에 놓인 orchestration 표면이 Team이라는 뜻이에요.
legacy swarm보다 Team을 먼저 이해해야 해요.
