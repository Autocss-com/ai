# ai — D7460N canonical laws (single source of truth)

The **one** place the D7460N laws live, for **every** project and **every** AI vendor.
Nothing here is repo-specific; nothing here names a tool.

- **[`AGENTS.md`](./AGENTS.md)** — the canonical laws: the **Response Integrity Charter**
  (`C0`–`C8`) + **D7460N Architecture** (`1`–`15`). This is what every repo points at.
- **[`.agents/skills/`](./.agents/skills/)** — the universal skills the laws route to
  (`architecture`, `html`, `css`, `javascript`, `json`, `data-flow`, `naming`, `security`,
  `pwa`), each with deep `references/`.

## How projects consume it

Clone once and import it from user-level memory — then every project on the machine
inherits the laws and skills automatically, with **no per-repo copy**:

```bash
git clone https://github.com/Autocss-com/ai ~/.claude/ai
# ~/.claude/CLAUDE.md  ->  @~/.claude/ai/AGENTS.md
git -C ~/.claude/ai pull      # refresh the laws for ALL projects at once
```

Each repo keeps only a thin pointer (`CLAUDE.md`, `.cursorrules`, Copilot instructions →
this file) plus its own **project-specific** `AGENTS.md` (structure, files, routing on top).

## Rules for editing

- **Edit the laws here, once.** Never copy or restate them in another repo — that creates
  drift. Change this file; every project follows.
- **Conflict priority:** this file > each repo's own `AGENTS.md` > that repo's
  `.agents/SESSION-HANDOFF.md`. On conflict, **surface it to the user — never resolve silently.**
