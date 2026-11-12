# Second Brain — Schema

An LLM-maintained wiki in the style of Karpathy's "LLM Wiki". Ian writes and drops material in; Claude compiles it into a linked wiki and answers questions from that wiki.

## Layers

| Layer | Owner | Rule |
|---|---|---|
| `raw/` | Ian | Source of truth. Claude reads but never edits content. Claude may move or rename a file only during ingest, and only from `raw/inbox/`. |
| `wiki/` | Claude | Compiled, interlinked pages. Ian rarely edits; if he does, Claude keeps his edits. |
| `CLAUDE.md` | Both | This file. Change it when a convention changes, not per task. |

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
```

Don't touch `.obsidian/`, `.git/`, `.trash/`, or `gemini-scribe/` (plugin data).

## Wiki pages

- One page per entity (company, person, client, project) or topic (process, offer, program). Prefer updating an existing page to creating a new one.
- Frontmatter, nothing more:
  ```yaml
  ---
  type: entity | topic | person
  updated: YYYY-MM-DD
  ---
  ```
- Body: short summary first, then facts. Every non-obvious claim links its source: `([[Raw Note Name]])`.
- Link other wiki pages with `[[page-name]]`. Use Obsidian wikilinks only, never markdown links to local files.
- When sources disagree, don't pick silently: record both under `## Open questions` with links.
- Keep pages under ~800 words. Split by subtopic when they grow.

## Operations

### Ingest ("ingest", "process inbox")
1. Read each new file in `raw/inbox/` (or the file Ian names).
2. Move it to its `raw/<domain>/` folder. Create a new domain folder only if nothing fits.
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
- Broken `[[links]]`; orphan wiki pages missing from `index.md`
- Contradictions or stale claims across pages
- Empty or zero-content notes in `raw/`: list them for Ian to delete. Never auto-delete.
Append a `lint` entry to `log.md`.

## Conventions
- Moving or renaming any file: update every `[[link]]` to it across the vault.
- Deleting: only with Ian's OK. git history is the backup, so there's no purge folder.
- Git: work on a feature branch and open a PR to `main`. Never commit to `main` directly.
