# Sync Log — oh-my-claudecode

## latest cycle

- previous source sha: `04655ee24207f367fee785b5eb33b21234d9e0e3`
- current source sha: `cf06566ddfff88e88f605499cd1a48609a6e7100`
- mode: `update`
- impact labels: README/소개, 설치/설정, CLI/명령어, 스킬/플러그인

## decision

origin 변경 파일을 기준으로 guide 문서의 관련 섹션을 다시 읽고 반영했습니다. 핵심 영향 영역: README/소개, 설치/설정, CLI/명령어, 스킬/플러그인.

## upstream commits reviewed

- `cf06566d Merge dev for v4.11.6 release`
- `28756531 chore(release): bump version to v4.11.6`
- `74edf7c2 Merge pull request #2604 from Yeachan-Heo/omx/issue-2602-ralph-prd-architect-gate`
- `f6507966 Close Ralph approval spoofing in reviewer-gated progression`
- `e122fcf0 Prevent Ralph from approving its own injected prompt text`
- `5481044d Prevent stale architect approvals from advancing Ralph stories`
- `bdf56347 Make Ralph startup PRD gating non-bypassable`
- `3213d01a Make Ralph enforce real PRD and story review gates`

## evidence

- source remote: `https://github.com/Yeachan-Heo/oh-my-claudecode.git`
- docs/interesting dirs: docs/, skills/, src/, tests/, examples/
- changed file sample:
- `.claude-plugin/marketplace.json`
- `.claude-plugin/plugin.json`
- `.clawhip/project.json`
- `.clawhip/state/prompt-submit.json`
- `.codex`
- `.github/release-body.md`
- `CHANGELOG.md`
- `README.md`
- `bridge/__pycache__/gyoshu_bridge.cpython-310.pyc`
- `bridge/cli.cjs`
- `bridge/mcp-server.cjs`
- `bridge/runtime-cli.cjs`
- `bridge/team-bridge.cjs`
- `bridge/team-mcp.cjs`
- `bridge/team.js`
- `dist/__tests__/auto-update.test.js`
- `dist/__tests__/auto-update.test.js.map`
- `dist/__tests__/background-cleanup-directory.test.js`
- `dist/__tests__/background-cleanup-directory.test.js.map`
- `dist/__tests__/bridge-help-question-regex.test.d.ts`
