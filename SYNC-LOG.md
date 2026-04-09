# Sync Log — oh-my-claudecode

## latest cycle

- previous source sha: `823f59ba4dfe3efd3518d99ad83156a11cdcb7b5`
- current source sha: `6b3cd060a954b122a4cd07eae71698aa415432f3`
- mode: `update`
- impact labels: README/소개, 설치/설정, CLI/명령어, 문서 구조, 스킬/플러그인, 소스코드, 테스트/검증

## decision

origin 변경 파일을 기준으로 guide 문서의 관련 섹션을 다시 읽고 반영했습니다. 핵심 영향 영역: README/소개, 설치/설정, CLI/명령어, 문서 구조, 스킬/플러그인, 소스코드, 테스트/검증.

## upstream commits reviewed

- `6b3cd060 chore(release): bump version to v4.11.2`
- `6746e503 fix(installer): prune duplicate agents and skills when plugin provides them (#2252)`
- `322459b0 Merge pull request #2359 from Yeachan-Heo/fix/setup-regression-tests`
- `14a89cd0 test(installer): add setup contract regression tests and stale cleanup`
- `67ec0065 Merge pull request #2352 from nextor2k/fix/worktree-project-identifier`
- `d372d6e9 Merge pull request #2349 from wwang2/fix/issue-2348-self-heal-node-path`
- `d9402565 Merge pull request #2356 from pgagarinov/feat/hud-plugin-root-envvar`
- `fc72b2f3 fix(hud): sort prerelease tags numerically in cache version comparator`

## evidence

- source remote: `https://github.com/Yeachan-Heo/oh-my-claudecode.git`
- docs/interesting dirs: docs/, skills/, src/, tests/, examples/
- changed file sample:
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
