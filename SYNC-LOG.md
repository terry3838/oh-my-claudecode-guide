# Sync Log — oh-my-claudecode

## latest cycle

- previous source sha: `fae376508355fb03ea6a2477453f37f0a59e707f`
- current source sha: `fae376508355fb03ea6a2477453f37f0a59e707f`
- mode: `guide-refresh`
- impact labels: frontdoor 재구성, 학습 흐름 강화, 용어 정리 강화, Mermaid 다이어그램 추가, Obsidian hybrid 출력 추가

## decision

이번 사이클은 upstream 코드 변경 반영보다 **가이드 품질 재작성**이 중심이었다.

기존 문서는 정보 자체는 있었지만, `pm-skills-guide` 수준의 교과서형 frontdoor와 학습 흐름을 만들기에는 구조가 약했다. 그래서 README / 학습 경로 / 용어집 / overview를 기준 문서형 구조로 재배치했다.

핵심 판단은 아래와 같다.

1. OMC는 기능 목록보다 **운영 런타임**으로 소개해야 한다.
2. 초심자는 `autopilot`보다도 결국 **Team을 중심축으로 이해**해야 한다.
3. `omc team`, hooks, `.omc/`, OpenClaw를 뒤로 미루더라도 문서 frontdoor에서는 존재감이 보여야 한다.
4. package naming 차이와 설치 경로 결 차이는 frontdoor에서 바로 짚어야 한다.

## guide changes

- `README.md`
  - 한 줄 정의, Claude Code와의 차이, 버전 기준, 핵심 표면, 자주 하는 오해, 추천 읽기 순서를 재구성
  - Mermaid 시스템 맵과 Obsidian companion pack 안내 추가
- `01-learning-paths.md`
  - 입문 → orchestration → 운영 → 확장/통합 → source reading의 5단계 학습 경로로 재작성
  - Mermaid 학습 순서 맵 추가
- `02-glossary.md`
  - 학습자가 실제로 헷갈리는 축 중심으로 용어 재정리
- `sections/01-overview.md`
  - 재작성 근거, upstream evidence, 문서 판단 기록 강화
- `assets/diagrams/`
  - Mermaid source (`.mmd`) 파일 추가
- `OBSIDIAN-VAULT-MAP.md`
  - repo guide와 vault notes 간 대응 관계 기록
- `obsidian/oh-my-claudecode Guide/`
  - MOC / Overview / Learning Paths / Glossary / Concepts / Workflows / References 노트 팩 추가

## upstream commits reviewed

- `fae37650 chore: update Discord invite link to OmO (Ultraworkers) server`
- `0ec792c0 chore: gitignore release-body.md to prevent stale release notes`
- `f93e27bc fix(release): add version sync hook + fix stale release body`
- `8660d291 fix(ci): sync version markers to 4.9.3`
- `884ec78d chore: bump version to 4.9.3`

## evidence

- source remote: `https://github.com/Yeachan-Heo/oh-my-claudecode.git`
- docs reviewed:
  - `README.md`
  - `docs/MIGRATION.md`
  - `docs/REFERENCE.md`
  - `docs/ARCHITECTURE.md`
  - `docs/OPENCLAW-ROUTING.md`
- source dirs reviewed:
  - `agents/`
  - `skills/`
  - `bridge/`
  - `src/team/`
  - `src/hooks/`
  - `src/openclaw/`
  - `src/notifications/`
  - `src/hud/`
  - `src/features/`
