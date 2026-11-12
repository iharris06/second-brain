# AGENTS — Operating Contract

Every agent (Claude, Codex, Cursor, …) reads this first. It is the only rules file; tool-specific files like `CLAUDE.md` just point here.

An LLM-maintained wiki in the style of Karpathy's "LLM Wiki". Ian writes and drops material in; the agent compiles it into a linked wiki and answers questions from that wiki.

## Layers

| Layer | Owner | Rule |
|---|---|---|
| `raw/` | Ian | Source of truth. Agents read but never edit content. An agent may move a file only during ingest, and only from `raw/inbox/`. |
| `wiki/` | Agent | Compiled, interlinked pages. Ian rarely edits; if he does, keep his edits. |
| `skills/` | Both | Reusable procedures: one folder per skill, with a `SKILL.md` plus its prompt files. |
| `AGENTS.md` | Both | This file. Change it when a convention changes, not per task. |

```
raw/
  inbox/      new captures land here (any format)
  mirk/       MIRK Technologies (agency)
  work/       day job (o3 = 1:1 notes)
  health/     training + nutrition
  projects/   side projects, one folder each
  assets/     PDFs, HTML, audio, images
wiki/
  index.md    catalog of every wiki page, one line each. Read this first.
  log.md      append-only history of ingest / query / lint
  *.md        flat, kebab-case pages
skills/
  <name>/SKILL.md
```

Don't touch `.obsidian/`, `.git/`, `.trash/`, or `gemini-scribe/` (plugin data).

## Secrets
Never put secrets in this repo: no API keys, passwords, tokens, account numbers, or client personal data beyond a name and business. Write where a secret lives ("Stripe key → 1Password"), never the secret itself. If one shows up in `raw/` or `inbox/`, stop and tell Ian.

## Wiki pages

- One page per entity (company, person, client, project) or topic (process, offer, program). Prefer updating an existing page to creating a new one.
- Frontmatter, nothing more:
  ```yaml
  ---
  type: entity | topic | person | canon
  summary: One sentence an agent reads to decide whether to open the page.
  updated: YYYY-MM-DD
  ---
  ```
- `canon` pages (e.g. [[mirk-positioning]], [[mirk-icp]]) hold Ian's decided answers. Agents only fill them from Ian's own words, never by inference; they write `TODO:` for anything undecided. When a source disagrees with canon, canon wins; note the conflict on the topic page.
- Body: facts. Every non-obvious claim links its source: `([[Raw Note Name]])`.
- Link other wiki pages with `[[page-name]]`. Use Obsidian wikilinks only, never markdown links to local files.
- When sources disagree, don't pick silently: record both under `## Open questions` with links.
- Keep pages under ~800 words. Split by subtopic when they grow.

## Operations

### Ingest ("ingest", "process inbox")
1. Read each new file in `raw/inbox/` (or the file Ian names).
2. Move it to its `raw/<domain>/` folder. Create a new domain folder only if nothing fits. A reusable prompt or procedure goes to `skills/<name>/` instead.
3. Update every affected wiki page (usually 1–5), creating pages only when needed.
4. Update `wiki/index.md`.
5. Append to `wiki/log.md`: `## [YYYY-MM-DD] ingest | <file> -> <pages touched>`
6. Briefly tell Ian what changed and flag any contradictions.

### Query (any question about Ian's notes)
1. Read `wiki/index.md`, then the relevant pages. Drop to `raw/` only for detail the wiki lacks.
2. Answer with `[[links]]` to the pages used.
3. If the answer is a reusable synthesis, offer to save it as a wiki page (and log it).

### Lint ("lint", or on a schedule)
Report first, then fix what's mechanical:
- Raw files not cited by any wiki page (not yet ingested)
- Broken `[[links]]`; orphan wiki pages missing from `index.md`; pages missing `summary`
- Contradictions or stale claims across pages, and `TODO:` items still open on canon pages
- Anything that looks like a secret
- Empty or zero-content notes in `raw/`: list them for Ian to delete. Never auto-delete.
Append a `lint` entry to `log.md`.

## Conventions
- Moving or renaming any file: update every `[[link]]` to it across the vault.
- Deleting: only with Ian's OK. git history is the backup, so there's no purge folder.
- Git: work on a feature branch and open a PR to `main`. Never commit to `main` directly.
