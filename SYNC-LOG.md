# Sync Log — oh-my-claudecode

## latest cycle

- previous source sha: `7b4a9e0435b7913de8942fa5a11d54eed7f1b85e`
- current source sha: `04655ee24207f367fee785b5eb33b21234d9e0e3`
- mode: `update`
- impact labels: README/소개, 설치/설정, CLI/명령어, 문서 구조, 스킬/플러그인, 소스코드

## decision

origin 변경 파일을 기준으로 guide 문서의 관련 섹션을 다시 읽고 반영했습니다. 핵심 영향 영역: README/소개, 설치/설정, CLI/명령어, 문서 구조, 스킬/플러그인, 소스코드.

## upstream commits reviewed

- `04655ee2 Merge pull request #2503 from Yeachan-Heo/dev`
- `5de9d4ba chore(release): fix docs/CLAUDE.md version marker for v4.11.5`
- `8a48b7a1 Merge pull request #2502 from Yeachan-Heo/omx-issue-2500-tmux-keyword-alert-noise`
- `545d1f3b chore(release): bump version to v4.11.5`
- `fb6584de Prevent prompt-mode startup echo from tripping tmux keyword alerts`
- `c3c48513 feat(release): rewrite release skill as generic repo-aware assistant (#2501)`
- `903e36a3 Merge pull request #2498 from Yeachan-Heo/omx-issue-2497-zero-backlog-followup-ux`
- `1d9ecedd Back off shipped idle follow-ups once zero backlog is unchanged`

## evidence

- source remote: `https://github.com/Yeachan-Heo/oh-my-claudecode.git`
- docs/interesting dirs: docs/, skills/, src/, tests/, examples/
- changed file sample:
- `.claude-plugin/marketplace.json`
- `.claude-plugin/plugin.json`
- `.github/release-body.md`
- `CONTRIBUTING.md`
- `README.md`
- `bridge/cli.cjs`
- `dist/__tests__/keyword-detector-script.test.js`
- `dist/__tests__/keyword-detector-script.test.js.map`
- `dist/__tests__/pre-tool-enforcer.test.js`
- `dist/__tests__/pre-tool-enforcer.test.js.map`
- `dist/__tests__/setup-claude-md-script.test.js`
- `dist/__tests__/setup-claude-md-script.test.js.map`
- `dist/cli/__tests__/launch.test.js`
- `dist/cli/__tests__/launch.test.js.map`
- `dist/cli/launch.d.ts.map`
- `dist/cli/launch.js`
- `dist/cli/launch.js.map`
- `dist/hooks/__tests__/bridge-routing.test.js`
- `dist/hooks/__tests__/bridge-routing.test.js.map`
- `dist/hooks/bridge.d.ts.map`
