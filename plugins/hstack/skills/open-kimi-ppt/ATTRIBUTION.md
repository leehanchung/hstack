# Attribution

This skill is vendored from [jinwyp/open-ppt-skill](https://github.com/jinwyp/open-ppt-skill)
(npm package `open-kimi-ppt-skill`), which is MIT licensed.

- Upstream version: `1.3.0`
- Upstream commit: `07eeaadcb04c32c9adb107eb5c8608e6be4e1008` (2026-08-07)
- Upstream path: `skills/open-kimi-ppt/`

## Local modifications

1. `reference/` renamed to `references/` (hstack convention); all internal path
   references updated.
2. `allowed-tools` added to the `SKILL.md` frontmatter (required by the Codex manifest).
3. Hardcoded `~/.agents/skills/open-kimi-ppt/scripts/...` command paths replaced with
   `"$SKILL_DIR"/scripts/...`, since the plugin installs outside `~/.agents/skills`.
4. The patched WASM exporter is vendored at `scripts/local-export/pptd_wasm_bg.wasm`
   (copied from the upstream package's `editor/neo-ppt/assets/pptd_wasm_bg-DPPWdROu.wasm`)
   so the default offline PPTX export works without the npm package.
5. A prerequisites note was added to `SKILL.md` step0 explaining that the ~270 MB offline
   neo-ppt editor mirror is **not** bundled, and that image QA / `--browser` / the manual
   editor need `OPEN_KIMI_PPT_EDITOR` to point at a copy of it.

Everything else — `SKILL.md` content, `references/`, `scripts/`, `tests/` — is upstream as-is.

## Upstream license

```
MIT License

Copyright (c) 2026 Binaryify Zhuang

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
