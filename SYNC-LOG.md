# Sync Log — oh-my-claudecode

## latest cycle

- previous source sha: `6b3cd060a954b122a4cd07eae71698aa415432f3`
- current source sha: `7b4a9e0435b7913de8942fa5a11d54eed7f1b85e`
- mode: `update`
- impact labels: README/소개, 설치/설정, CLI/명령어, 스킬/플러그인

## decision

origin 변경 파일을 기준으로 guide 문서의 관련 섹션을 다시 읽고 반영했습니다. 핵심 영향 영역: README/소개, 설치/설정, CLI/명령어, 스킬/플러그인.

## upstream commits reviewed

- `7b4a9e04 Merge pull request #2420 from Yeachan-Heo/dev`
- `b1dcbc35 fix(release): sync marketplace.json, docs/CLAUDE.md, and package-lock to 4.11.4`
- `2e880952 chore(release): bump version to v4.11.4`
- `dc3e9724 fix(team): preserve forceInherit by skipping worker model resolution (#2418)`
- `06ea4ed3 fix(hud): try older built cache versions when latest import fails (#2416)`
- `dc2f9629 fix(installer): use portable hook command paths on Windows (#2415)`
- `8523b071 fix(preemptive-compaction): fallback to hook context window usage (#2412)`
- `e26648fe fix(keyword-detector): narrow false-positive suppression for #2390 (#2411)`

## evidence

- source remote: `https://github.com/Yeachan-Heo/oh-my-claudecode.git`
- docs/interesting dirs: docs/, skills/, src/, tests/, examples/
- changed file sample:
- `.claude-plugin/marketplace.json`
- `.claude-plugin/plugin.json`
- `.github/release-body.md`
- `CHANGELOG.md`
- `CONTRIBUTING.md`
- `README.de.md`
- `README.es.md`
- `README.fr.md`
- `README.it.md`
- `README.ja.md`
- `README.ko.md`
- `README.md`
- `README.pt.md`
- `README.ru.md`
- `README.tr.md`
- `README.vi.md`
- `README.zh.md`
- `bridge/cli.cjs`
- `bridge/mcp-server.cjs`
- `bridge/runtime-cli.cjs`
