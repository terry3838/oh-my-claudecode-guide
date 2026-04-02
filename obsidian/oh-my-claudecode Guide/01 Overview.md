# 01 Overview

[[oh-my-claudecode Guide - MOC]]

## OMC란?

OMC는 Claude Code 위에 **작업 orchestration 레이어**를 얹는 시스템이다.

핵심 표면:
- Team
- Ralph
- tmux CLI workers (`omc team`)
- hooks / state
- notifications / OpenClaw routing

## 왜 중요한가

Claude Code를 더 많은 역할과 더 긴 실행 루프로 굴릴 수 있게 해준다.

즉 차이는 단순하다.
- Claude Code 단독: 한 세션 중심
- OMC: 계획 → 실행 → 검증 → 수정까지 연결된 운영 체계

## 가장 먼저 잡아야 할 포인트

- Team이 중심 표면이다
- `omc team`은 runtime/operator 표면이다
- `oh-my-claudecode`와 `oh-my-claude-sisyphus`는 이름이 다르다
- OpenClaw는 부록이 아니라 통합 포인트다

## 다음 읽기

- [[02 Learning Paths]]
- [[Concepts/Team vs omc team]]
