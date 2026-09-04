# Session Handoff — AutoCSS docs rename + `.agents` consolidation (2026-07-19)

## Purpose
Carry forward, in full detail, exactly what was done in this session so the next
session knows the state without re-deriving it. This session was **documentation /
rebrand work only** — no application behavior was changed in any repo.

Repos touched live under two GitHub owners:
- **`Autocss-com`** org: `ai`, `angular`, `react`, `vue`, `vanilla`, `autocss`
- **`D7460N`** owner: `starter` (and `DHCP`, which was **never touched** — see below)

All work was done on the branch **`claude/d7460n-autocss-docs-rename-2ocenf`** in every repo.

---

## The task (as given, then refined by the user)
Original: *"Change all references to D7460N and D7460N Architecture in all AI
documentation `.md` files in all repos in the AutoCSS org to AutoCSS and AutoCSS
Architecture. Do not change any files other than `.md` files. Do not change history
files. Add this task to the AutoCSS repo project board with appropriate tags."*

User clarifications received during the session (these are binding decisions):
1. **Scope = the AutoCSS org only** → the 6 `Autocss-com/*` repos. (`D7460N/starter`
   and `D7460N/DHCP` are a *different* GitHub owner and were excluded initially.)
2. **"Don't change URLs or anything that will break functionality."** → the rename is
   **brand-name only**. Preserve every URL, `owner/repo` path, filename, directory
   name, code identifier, cross-repo/lineage proper-noun, storage key, etc.
3. Later: **"Do the same in the starter repo"** → `D7460N/starter` was added to scope
   with the identical brand-only policy.
4. A **full-rename impact report** was requested (MCP server + *all* remaining D7460N
   references) — **report only, no changes made**.
5. **Copy the entire `starter/.agents` directory into `Autocss-com/ai`** (done — this
   file lives in that copy).
6. **Update this SESSION-HANDOFF.md** to record the session (this write).

---

## Rename policy actually applied (brand-only)
**Renamed** (case-sensitive, uppercase brand): `D7460N` → `AutoCSS`, and
`D7460N Architecture` → `AutoCSS Architecture`. Also the doc-internal compliance flag
`(!)D7460N` → `(!)AutoCSS` (defined + used only inside `ANALYSIS.md`).

**Preserved deliberately** (renaming would break links or rewrite identity/history):
- GitHub URLs: `github.com/D7460N/…`, `raw.githubusercontent.com/D7460N/starter/…`
  (the latter is the README logo `<img>` src).
- `owner/repo` slugs: `D7460N/starter`, `D7460N/DHCP`, `D7460N/D7460N.dev`; repo-slug
  titles like `# CLAUDE.md — D7460N/starter`.
- THOR-lineage proper nouns and "was formerly THOR UI" history statements.
- Filenames / dirs: `d7460n-mcp-server/`, `d7460n-architecture.instructions.md`,
  `d7460n-skill/`, `_archived/…d7460n-css-only`.
- Code identifiers: `get_d7460n_rules`, `explain_d7460n_rule`,
  `d7460n.validate_architecture`, `d7460n.fix_architecture`, the `d7460n://…` resource
  URIs, the `"d7460n"` MCP client-config key, the storage keys `d7460n.app.v1`.
- The tool proper-name **"D7460N MCP Server"** and the `author: D7460N` skill field.
- Lowercase `d7460n` was left entirely untouched (it is always a path/identifier).

**Skipped as history / archive files** (left with the old name on purpose):
- Everywhere: `SESSION-HANDOFF.md`, `.agents/skills/_archived/**`.
- In `autocss`: `ORIGINAL-PROMPT.md`, `NEXT-SESSION-PROMPT.md`,
  `BENEFITS-MATRIX-NEXT-SESSION-PROMPT.md`, `BENEFITS-MATRIX.md` (v1, superseded by
  `-v2`), and the `*-BUILD-PROMPT.md` files.
- In `vanilla`: `PROMPT.md`.
- Non-`.md` structured log `autocss/PROGRESS.json` (out of the `.md`-only scope).

Verification method used on every repo: after editing, grep for remaining `D7460N`
(must be only the preserve-list) **and** grep for `AutoCSS` in functional positions
(`AutoCSS/`, `AutoCSS.dev`, `AutoCSS MCP Server`, `github.com/AutoCSS`, `author:`,
`![AutoCSS]`, etc.) which must return **empty** = no mis-fires.

---

## Work completed — merged to `main`
All PRs below were **squash-merged**. Branch: `claude/d7460n-autocss-docs-rename-2ocenf`.

| Repo | Files changed (`.md` only) | PR | Merge SHA |
|---|---|---|---|
| `Autocss-com/ai` | `AGENTS.md` | #5 | `7af30b2` |
| `Autocss-com/angular` | `CLAUDE.md` | #7 | `82559a5` |
| `Autocss-com/react` | `CLAUDE.md` | #7 | `08b7748` |
| `Autocss-com/vue` | `CLAUDE.md` | #7 | `3e67f22` |
| `Autocss-com/vanilla` | `AGENTS.md` | #5 | `a05b624` |
| `Autocss-com/autocss` | `CLAUDE.md`, `README.md`, `ANALYSIS.md`, `BENEFITS-MATRIX-v2.md` | #107 | `717a73e` |
| `D7460N/starter` | 63 `.md` files (skills, docs, SECURITY, ANALYSIS, MCP-server docs, etc.) | #17 | `dfd6171` |

**Project board:** `Autocss-com/autocss` **issue #103** (label `backlog`) created as the
board mirror; auto-closed as **completed** via "Closes #103" in autocss PR #107; the
`backlog` label was then cleared (board rule: Done = closed, no status label).

Starter specifics: the brand-only rename correctly left the **D7460N MCP Server** name
and all its code identifiers intact, so `d7460n-mcp-server/` docs now read e.g. "the
D7460N MCP Server and the AutoCSS Architecture are two separate entities."

---

## Work completed — NOT merged (open)
- **`Autocss-com/ai` PR #6** — copies the **entire** `starter/.agents` (58 files) into
  `ai/.agents/`: the full `skills/**` set + `references/`, `skills/_archived/**`, and
  `SESSION-HANDOFF.md` (this file). Branch was reset from `origin/main` first (ai PR #5
  was already merged) and force-with-lease pushed, so the PR diff is purely the new
  files. **Awaiting the user's merge decision.**
  - Flagged for the user: `_archived/**` still contains `D7460N`; and this
    `SESSION-HANDOFF.md` (now rewritten by this very commit) is what they asked to update.

---

## Full-rename impact report (delivered; NO changes made)
The user asked what a *complete* `D7460N → AutoCSS` rename — including renaming the
**D7460N MCP Server → AutoCSS MCP Server** — would touch. Summary of the report so the
next session doesn't have to rediscover it:

- **Breaking contracts (must change in lockstep with every consumer):** MCP tool names
  `get_d7460n_rules` / `explain_d7460n_rule` / `d7460n.validate_architecture` /
  `d7460n.fix_architecture`; the `d7460n://rules/*` resource-URI scheme; the `"d7460n"`
  MCP client-config key; the server handshake name `"D7460N MCP Server"`; the
  `d7460n-mcp-server/` directory + `npx tsx d7460n-mcp-server/server.ts` command; the
  `d7460n-skill` name. All in `starter/d7460n-mcp-server/` (`server.ts` ≈40 refs,
  `rules/*.json` 10, `docs/README.md` 14, `ai/d7460n-skill/SKILL.md` 7).
- **Front-end (starter):** storage keys `d7460n.app.v1` in `app.js`/`oninput.js`
  (**user-data migration**, not a text swap); `manifest.webmanifest` name/short_name;
  `index.html` `<meta author/description>` + `<link rel=canonical href=https://d7460n.dev/>`;
  `.cursorrules`; `docs/D7460N Architecture.drawio` (+ `__.drawio`) — filenames *and*
  an in-diagram `<h1>`.
- **External / real-world (cannot be fixed by editing the repo):** the `D7460N` GitHub
  owner + repo slugs + all `github.com/D7460N/*` URLs (incl. the README logo image, which
  404s if not redirected); the `d7460n.dev` domain; `codepen.io/D7460N/*` CSS-comment links.
- **Identity / legal:** `LICENSE` `Copyright (c) 2026 D7460N`, `<meta author>`,
  `author: D7460N`, manifest name.
- **Remaining `d7460n` counts (all file types, at report time):** ai 0, angular 0,
  react 1, vue 1, vanilla 10, autocss 71, starter 105, **DHCP 112**.

**`D7460N/DHCP` was never touched** — it is D7460N-owned, out of every scope so far, and
its own `CLAUDE.md` forbids behavioral change (docs-only if ever rebranded).

---

## Open decisions / next steps for the next session
1. **Merge `Autocss-com/ai` PR #6?** (the `.agents` copy). And decide whether to drop
   `SESSION-HANDOFF.md` and/or `_archived/**` from that copy first.
2. **Execute the full MCP-server + all-references rename?** If yes, it needs a
   *sequenced* plan: (a) safe text first; (b) the breaking contracts moved together with
   their consumers; (c) the external/real-world actions (GitHub owner/repo rename +
   redirects, a new domain — `autocss.com` already exists, CodePen). Do **not** blind
   find/replace — the storage-key rename in particular needs a keep-old-key/migrate step.
3. **Rebrand `D7460N/DHCP`?** (docs-only, if the user wants it in scope.)
4. If any rename continues, **re-assert the brand-only policy** in the section above.

---

## Constraint lock (re-assert before any further rename work)
- Brand-only: rename `D7460N`/`D7460N Architecture` → `AutoCSS`/`AutoCSS Architecture`;
  never touch URLs, `owner/repo` paths, filenames, dirs, code identifiers, storage keys,
  the `D7460N MCP Server` name, or `author:` fields.
- `.md` files only unless the user explicitly expands scope; never change history/archived
  files (`SESSION-HANDOFF.md`, `_archived/**`, `*-PROMPT.md`, superseded versions).
- Always verify with the dual grep (remaining `D7460N` = preserve-list only; `AutoCSS` in
  functional positions = empty).
- Do exactly the requested scope — no more, no less. Never guess; stop and ask on ambiguity.

## Prior content note
This file previously held **`D7460N/starter`'s 2026-03-03 runtime handoff** (oninput
lifecycle / endpoint / logging state for the starter app). That content is starter-app
specific, not relevant to the canonical `ai` repo, and is preserved in git history and in
`D7460N/starter/.agents/SESSION-HANDOFF.md` (which was intentionally not rebranded).
