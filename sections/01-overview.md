# oh-my-claudecode 개요

## 원본 저장소 역할

- repo: `oh-my-claudecode`
- source: `https://github.com/Yeachan-Heo/oh-my-claudecode.git`
- latest synced commit: `2487d3878f8d`
- summary: English | [한국어](README.ko.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Español](README.es.md) | [Tiếng Việt](README.vi.md) | [Português](README.pt.md)

## 이번 싸이클 판단

- sync mode: `update`
- impact labels: 설치/설정, CLI/명령어, 문서 구조, 스킬/플러그인, 소스코드, 테스트/검증
- 판단: origin 변경 파일을 기준으로 guide 문서의 관련 섹션을 다시 읽고 반영했습니다. 핵심 영향 영역: 설치/설정, CLI/명령어, 문서 구조, 스킬/플러그인, 소스코드, 테스트/검증.

## 최근 upstream 커밋

- `2487d387 Merge pull request #2162 from Yeachan-Heo/release/4.10.2`
- `1fe4f160 Unblock the 4.10.2 release path`
- `81d153ef Merge pull request #2146 from Yeachan-Heo/issue-2143-omc-launch-followup`
- `42b92f6f feat(hud): add configurable call count icon format (#2151)`
- `80d1cae2 fix: resolve global HUD npm package lookup outside Node projects (#2149)`
- `25f3e2de fix: force-load omc claude config on omc launch`

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
