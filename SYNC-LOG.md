# Sync Log — oh-my-claudecode

## latest cycle

- previous source sha: `2487d3878f8d25e60802940b020d5ee8774d135e`
- current source sha: `823f59ba4dfe3efd3518d99ad83156a11cdcb7b5`
- mode: `update`
- impact labels: README/소개, 설치/설정, CLI/명령어, 스킬/플러그인, 테스트/검증

## decision

origin 변경 파일을 기준으로 guide 문서의 관련 섹션을 다시 읽고 반영했습니다. 핵심 영향 영역: README/소개, 설치/설정, CLI/명령어, 스킬/플러그인, 테스트/검증.

## upstream commits reviewed

- `823f59ba chore(release): bump version to v4.11.1`
- `3e80dac6 fix(installer): use getPackageDir() instead of __dirname for HUD helper copies (#2347)`
- `ec9398d7 Merge pull request #2331 from shaun0927/fix/hardmax-iterations-bypass`
- `9b340a8a fix(security): clamp hardMaxIterations and enforce in autopilot`
- `d716a30d Merge pull request #2247 from pgagarinov/feat/hud-git-status`
- `e3b04e45 Merge pull request #2333 from shaun0927/fix/team-registration-locks`
- `cb653014 feat(hud): add git working tree status element`
- `d671cecb fix(team): wrap withFileLockSync in try/catch for lock contention safety`

## evidence

- source remote: `https://github.com/Yeachan-Heo/oh-my-claudecode.git`
- docs/interesting dirs: docs/, skills/, src/, tests/, examples/
- changed file sample:
- `.claude-plugin/marketplace.json`
- `.claude-plugin/plugin.json`
- `.github/release-body.md`
- `.github/workflows/release.yml`
- `CHANGELOG.md`
- `README.md`
- `bridge/cli.cjs`
- `bridge/mcp-server.cjs`
- `bridge/runtime-cli.cjs`
- `bridge/team-bridge.cjs`
- `bridge/team-mcp.cjs`
- `bridge/team.js`
- `dist/__tests__/auto-update.test.js`
- `dist/__tests__/auto-update.test.js.map`
- `dist/__tests__/cli-config-stop-callback.test.js`
- `dist/__tests__/cli-config-stop-callback.test.js.map`
- `dist/__tests__/delegation-enforcement-levels.test.js`
- `dist/__tests__/delegation-enforcement-levels.test.js.map`
- `dist/__tests__/doctor-conflicts.test.js`
- `dist/__tests__/doctor-conflicts.test.js.map`
