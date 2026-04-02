# Team vs omc team

[[oh-my-claudecode Guide - MOC]]

## 핵심 차이

| 표면 | 의미 |
|---|---|
| `/team` | 사용자/학습자가 보는 canonical orchestration surface |
| `omc team` | 운영자/runtime가 보는 tmux CLI worker surface |

## 왜 이 구분이 중요한가

이 둘을 같은 것으로 보면 OMC를 단순 명령 별칭 집합으로 오해한다.

실제로는:
- Team은 **생명주기 orchestration**에 가깝고
- `omc team`은 **실제 worker 운영**에 가깝다

## Team pipeline

```text
team-plan → team-prd → team-exec → team-verify → team-fix
```

```mermaid
flowchart LR
    subgraph A[/team]
        A1[canonical orchestration]
        A2[pipeline lifecycle]
    end
    subgraph B[omc team]
        B1[tmux runtime]
        B2[real CLI workers]
    end
    A <--> B
```

## 같이 읽을 노트

- [[02 Learning Paths]]
- [[References/Source Map]]
