# Light_line Folder Alignment Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 鎶?`Light_line` 浠庘€滃睍绀洪〉閲屽唴宓岀殑鎻掍欢鑽夊浘鈥濇敹鏁涙垚鍜?`pm-skills` 瀵归綈鐨勫疄浣撴彃浠剁洰褰曪紝鏈€缁堝湪浠撳簱涓湡瀹炶惤鍑?`.codex-plugin/`, `commands/`, `hooks/`, `skills/`, `workflows/`銆?
**Architecture:** 浠?`C:\Users\Admin\Light_line\plugins\light-line` 浣滀负鍐呭婧愪笌缁撴瀯鍙傜収锛屼粨搴撴牴鐩綍淇濈暀鐜版湁娴忚鍣ㄥ寲鎵撳寘鐣岄潰锛岃€岀湡姝ｅ彲瀹夎鐨勬彃浠舵爲鏀惧埌 `plugins/light-line/` 涓嬨€傚睍绀洪〉涓嶅啀鎶?commands/hooks 褰撴垚鎶借薄姒傚康锛岃€屾槸浠庤繖妫电湡瀹炵洰褰曟爲璇诲彇鎴栧悓姝ュ嚭娓呭崟銆佽鏁板拰棰勮銆?
**Tech Stack:** PowerShell, existing HTML/CSS/JS app, Codex plugin manifest format, Markdown, Node `.mjs` hooks.

## Global Constraints

- Keep the canonical plugin tree aligned to `pm-skills`-style folders: `.codex-plugin/`, `commands/`, `hooks/`, `skills/`, `workflows/`.
- Preserve the current Light_line UI shell; do not remove the browser-based packaging experience.
- Treat `plugins/light-line/` as the source of truth for installable plugin contents.
- Keep `plugin.json` conservative: do not add unsupported manifest fields just to describe `commands` or `hooks`.
- Final counts must remain `18 Skills`, `5 Commands`, `4 Hooks`.

---

### Task 1: Materialize the canonical plugin tree

**Files:**
- Create: `plugins/light-line/.codex-plugin/plugin.json`
- Create: `plugins/light-line/commands/README.md`
- Create: `plugins/light-line/commands/new-frontend-feature.md`
- Create: `plugins/light-line/commands/refactor-window-module.md`
- Create: `plugins/light-line/commands/connect-bff-rag.md`
- Create: `plugins/light-line/commands/optimize-motion-timeline.md`
- Create: `plugins/light-line/commands/delivery-review.md`
- Create: `plugins/light-line/hooks/hooks.json`
- Create: `plugins/light-line/hooks/session-start.mjs`
- Create: `plugins/light-line/hooks/user-prompt-submit.mjs`
- Create: `plugins/light-line/hooks/pre-tool-use.mjs`
- Create: `plugins/light-line/hooks/post-tool-use.mjs`
- Create: `plugins/light-line/hooks/README.md`
- Create: `plugins/light-line/skills/bff-route-governance/SKILL.md`
- Create: `plugins/light-line/skills/chat-history-layout-refactor/SKILL.md`
- Create: `plugins/light-line/skills/chat-initial-state-optimization/SKILL.md`
- Create: `plugins/light-line/skills/database-window-governance/SKILL.md`
- Create: `plugins/light-line/skills/fastapi-mia-rag-integration/SKILL.md`
- Create: `plugins/light-line/skills/federation-chat-integration/SKILL.md`
- Create: `plugins/light-line/skills/frontend-component-mistake-book/SKILL.md`
- Create: `plugins/light-line/skills/frontend-motion-mistake-book/SKILL.md`
- Create: `plugins/light-line/skills/frontend-stack-mistake-book/SKILL.md`
- Create: `plugins/light-line/skills/frontend-timeline-mistake-book/SKILL.md`
- Create: `plugins/light-line/skills/frontend-ui-mistake-book/SKILL.md`
- Create: `plugins/light-line/skills/macro-window-governance/SKILL.md`
- Create: `plugins/light-line/skills/noob-deployment-tutorial/SKILL.md`
- Create: `plugins/light-line/skills/repo-delivery-governance/SKILL.md`
- Create: `plugins/light-line/skills/shared-component-governance/SKILL.md`
- Create: `plugins/light-line/skills/trace-graph-physics-optimization/SKILL.md`
- Create: `plugins/light-line/skills/window-module-boundary/SKILL.md`
- Create: `plugins/light-line/skills/window4-chat-governance/SKILL.md`
- Create: each skill folder's `agents/openai.yaml` companion
- Create: `plugins/light-line/workflows/*.md` for the 5 workflow docs already defined in `catalog.js`
- Create: `plugins/light-line/README.md`
- Create: `plugins/light-line/鎶€鑳界储寮?md`

**Interfaces:**
- Consumes: the current content in `catalog.js` and the existing reference tree at `C:\Users\Admin\Light_line\plugins\light-line`
- Produces: a real plugin directory that matches the pm-skills-shaped structure the UI claims to package

- [ ] **Step 1: Copy the authoritative plugin content into `plugins/light-line/`**

Use the existing final plugin tree as the source map for the folder names and file inventory.

- [ ] **Step 2: Verify the tree shape**

Run:
```powershell
Get-ChildItem -Force -Recurse .\plugins\light-line
```
Expected:
`18` skill folders, `5` command files, `4` hook files, `5` workflow files, and `1` `.codex-plugin/plugin.json`.

- [ ] **Step 3: Confirm install-facing metadata stays valid**

Run:
```powershell
Get-Content -Encoding UTF8 .\plugins\light-line\.codex-plugin\plugin.json
```
Expected:
plugin name remains `light-line`, and no unsupported manifest fields are introduced.

### Task 2: Repoint the UI data model at the real plugin tree

**Files:**
- Modify: `catalog.js`
- Modify: `app.js`

**Interfaces:**
- Consumes: `plugins/light-line/` from Task 1
- Produces: a catalog layer that reflects the real plugin tree instead of a large hard-coded inline blob

- [ ] **Step 1: Replace the brittle inline source blob with generated or filesystem-backed inventory data**

Keep the same UI contract, but source the counts and paths from the canonical folder.

- [ ] **Step 2: Make the graph and counters read the real folder inventory**

The UI should still show `18 / 5 / 4`, but now those numbers must come from the folder tree, not from a hand-edited copy.

- [ ] **Step 3: Re-run the page locally and confirm the counts match the folder**

Open the page and verify the selection panel, graph, and footer all agree on the same inventory.

### Task 3: Reconcile the prose so it matches the new structure

**Files:**
- Modify: `README.md`
- Modify: `index.html`

**Interfaces:**
- Consumes: the canonical tree from Task 1 and the data model from Task 2
- Produces: user-facing copy that no longer contradicts the actual plugin layout

- [ ] **Step 1: Remove the 鈥渃ommands are only templates鈥?contradiction**

Explain `commands/` as a real plugin folder while keeping any note about Codex runtime behavior accurate and explicit.

- [ ] **Step 2: Update the install and boundary text**

Make the README and page copy say that the repo carries an installable plugin tree, not just a showcase.

- [ ] **Step 3: Refresh the visible counts and labels**

Ensure the page headline, plugin facts, and supporting copy still match the final tree shape after the sync.

### Task 4: Verify the package as a plugin, not just as a page

**Files:**
- Test: `plugins/light-line/**`
- Test: `catalog.js`
- Test: `app.js`
- Test: `README.md`

**Interfaces:**
- Consumes: the updated folder tree and UI model
- Produces: a verified Light_line plugin package that can be inspected as a pm-skills-style directory

- [ ] **Step 1: Count the folders and top-level capabilities**

Run:
```powershell
Get-ChildItem -Directory .\plugins\light-line\skills | Measure-Object
Get-ChildItem -File .\plugins\light-line\commands | Measure-Object
Get-ChildItem -File .\plugins\light-line\hooks | Where-Object { $_.Name -match '\.mjs$' } | Measure-Object
```
Expected:
`18` skill folders, `5` command files, `4` hook scripts.

- [ ] **Step 2: Check the UI still renders the package summary**

Open the page and confirm the graph, counters, and preview pane still work after the data source swap.

- [ ] **Step 3: Package acceptance**

Confirm the repo now tells one consistent story: the folder tree, the manifest, and the UI all describe the same installable plugin.

