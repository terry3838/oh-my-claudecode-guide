# Sync Log — oh-my-claudecode

## latest cycle

- previous source sha: `e3509365cfc264228c68c417d39c45d5b4df70cb`
- current source sha: `2487d3878f8d25e60802940b020d5ee8774d135e`
- mode: `update`
- impact labels: 설치/설정, CLI/명령어, 문서 구조, 스킬/플러그인, 소스코드, 테스트/검증

## decision

origin 변경 파일을 기준으로 guide 문서의 관련 섹션을 다시 읽고 반영했습니다. 핵심 영향 영역: 설치/설정, CLI/명령어, 문서 구조, 스킬/플러그인, 소스코드, 테스트/검증.

## upstream commits reviewed

- `2487d387 Merge pull request #2162 from Yeachan-Heo/release/4.10.2`
- `1fe4f160 Unblock the 4.10.2 release path`
- `81d153ef Merge pull request #2146 from Yeachan-Heo/issue-2143-omc-launch-followup`
- `42b92f6f feat(hud): add configurable call count icon format (#2151)`
- `80d1cae2 fix: resolve global HUD npm package lookup outside Node projects (#2149)`
- `25f3e2de fix: force-load omc claude config on omc launch`
- `0d836e64 fix: preserve existing global CLAUDE.md during setup (#2144)`
- `954f998a Preserve team worker pane width and bundled agent path resolution (#2137)`

## evidence

- source remote: `https://github.com/Yeachan-Heo/oh-my-claudecode.git`
- docs/interesting dirs: docs/, skills/, src/, tests/, examples/
- changed file sample:
- `.claude-plugin/marketplace.json`
- `.claude-plugin/plugin.json`
- `.github/CLAUDE.md`
- `.github/release-body.md`
- `.github/workflows/pr-check.yml`
- `.gitignore`
- `CHANGELOG.md`
- `bridge/cli.cjs`
- `bridge/mcp-server.cjs`
- `bridge/runtime-cli.cjs`
- `bridge/team-mcp.cjs`
- `bridge/team.js`
- `dist/__tests__/bedrock-lm-suffix-hook.test.js`
- `dist/__tests__/bedrock-lm-suffix-hook.test.js.map`
- `dist/__tests__/hud-marketplace-resolution.test.js`
- `dist/__tests__/hud-marketplace-resolution.test.js.map`
- `dist/__tests__/hud/call-counts.test.js`
- `dist/__tests__/hud/call-counts.test.js.map`
- `dist/__tests__/hud/git.test.js`
- `dist/__tests__/hud/git.test.js.map`
