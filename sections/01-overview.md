# oh-my-claudecode 개요

## 원본 저장소 역할

- repo: `oh-my-claudecode`
- source: `https://github.com/Yeachan-Heo/oh-my-claudecode.git`
- latest synced commit: `6b3cd060a954`
- summary: English | [한국어](README.ko.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Español](README.es.md) | [Tiếng Việt](README.vi.md) | [Português](README.pt.md)

## 이번 싸이클 판단

- sync mode: `update`
- impact labels: README/소개, 설치/설정, CLI/명령어, 문서 구조, 스킬/플러그인, 소스코드, 테스트/검증
- 판단: origin 변경 파일을 기준으로 guide 문서의 관련 섹션을 다시 읽고 반영했습니다. 핵심 영향 영역: README/소개, 설치/설정, CLI/명령어, 문서 구조, 스킬/플러그인, 소스코드, 테스트/검증.

## 최근 upstream 커밋

- `6b3cd060 chore(release): bump version to v4.11.2`
- `6746e503 fix(installer): prune duplicate agents and skills when plugin provides them (#2252)`
- `322459b0 Merge pull request #2359 from Yeachan-Heo/fix/setup-regression-tests`
- `14a89cd0 test(installer): add setup contract regression tests and stale cleanup`
- `67ec0065 Merge pull request #2352 from nextor2k/fix/worktree-project-identifier`
- `d372d6e9 Merge pull request #2349 from wwang2/fix/issue-2348-self-heal-node-path`

## 확인한 원본 구조

- `.claude-plugin/`
- `.mcp.json`
- `.npmignore`
- `agents/`
- `AGENTS.md`
- `assets/`
- `benchmark/`
- `benchmarks/`
- `bridge/`
- `CHANGELOG.md`
- `CLAUDE.md`
- `dist/`
- `docs/`
- `eslint.config.js`
- `examples/`
- `hooks/`
- `LICENSE`
- `missions/`
- `package-lock.json`
- `package.json`

## guide 업데이트 포인트

- README 관리 블록 갱신
- `UPSTREAM-SNAPSHOT.md` 갱신
- `SYNC-LOG.md` 갱신
- 개요 문서 재작성

## 변경 파일 샘플

- `.claude-plugin/marketplace.json`
- `.claude-plugin/plugin.json`
- `.github/workflows/release.yml`
- `README.md`
- `docs/CLAUDE.md`
- `package-lock.json`
- `package.json`
- `scripts/lib/hud-wrapper-template.mjs`
- `scripts/lib/hud-wrapper-template.txt`
- `scripts/plugin-setup.mjs`
- `src/__tests__/hud-build-guidance.test.ts`
- `src/__tests__/hud-marketplace-resolution.test.ts`
- `src/__tests__/hud-windows.test.ts`
- `src/__tests__/hud-wrapper-template-sync.test.ts`
- `src/__tests__/hud/state.test.ts`
- `src/__tests__/paths-consistency.test.ts`
- `src/__tests__/plugin-setup-devpaths.test.ts`
- `src/__tests__/session-start-cache-cleanup.test.ts`
- `src/__tests__/setup-contracts-regression.test.ts`
- `src/__tests__/task-continuation.test.ts`
