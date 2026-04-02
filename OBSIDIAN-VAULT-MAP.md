# Obsidian Vault Map

이 문서는 `oh-my-claudecode-guide` 의 repo guide 문서를 Obsidian note pack과 어떻게 대응시키는지 정리한다.

## 출력 모드

- mode: `hybrid`
- repo guide: `oh-my-claudecode-guide/`
- repo-local note pack: `obsidian/oh-my-claudecode Guide/`
- live vault target: `unset`
- live sync status: `not applied`

## 안전 원칙

- repo-local pack이 정본이다.
- live vault sync는 **의도된 vault target이 명시적으로 확인된 뒤에만** 수행한다.
- default vault나 CLI 반환값은 참고 정보일 뿐, 목적지 확정 근거가 아니다.

## 매핑

| repo guide | note pack |
|---|---|
| `README.md` | `oh-my-claudecode Guide/oh-my-claudecode Guide - MOC.md` |
| `01-learning-paths.md` | `oh-my-claudecode Guide/02 Learning Paths.md` |
| `02-glossary.md` | `oh-my-claudecode Guide/03 Glossary.md` |
| `sections/01-overview.md` | `oh-my-claudecode Guide/01 Overview.md` |
| `sections/02-team-runtime-and-worker-model.md` | `oh-my-claudecode Guide/Concepts/Team runtime and worker model.md` |
| `sections/03-hooks-openclaw-and-observability.md` | `oh-my-claudecode Guide/Concepts/Hooks openclaw and observability.md` |

## note map 의도

- MOC가 frontdoor 역할을 한다.
- Learning Paths / Glossary가 기본 3축이 된다.
- deep dive는 source-backed reading surface로 붙인다.
- References와 Workflows는 길찾기/증거를 붙잡아 둔다.
