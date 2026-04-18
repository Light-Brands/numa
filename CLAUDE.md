# NUMA — Claude Code Notes

**Read [`AGENTS.md`](./AGENTS.md) first.** This file only adds Claude-specific notes.

## Session start

1. `git log --oneline -5` to see what changed since the last session. Currently a single seed commit on `main` (`5eb8eda`); any new history is real work.
2. Skim `README.md`, then go directly to whichever of the two project trees the user named (`docs/01-malta-repayment/` or `docs/02-costa-rica-development/`). Don't read both unless asked.
3. There is no `CHANGELOG.md` or `TODO.md`. Open questions live inline in the docs as `### Key Structuring Questions`, `## Critical Questions to Resolve`, and `[ ]` checklist items. Treat those as the TODO list.

## Worktree rule

This is a markdown-only repo with no build, no tests, no dev server. Concurrent sessions racing the `.git/index` is the only collision risk.

- **Skip the worktree** for single-paragraph edits, typo fixes, or any single-session task you'll commit in <2 minutes.
- **Use `bin/qie worktree auto numa-<slug>`** (run from QIE root) before any multi-file rewrite, restructuring, or session you expect to share with another open Claude window. Idempotent.

## Editing discipline

- This is a research-and-planning vault for live cross-border deals (see AGENTS.md "What this is"). Sloppy phrasing has real downstream cost — the principal may act on what you write within days. Be precise; flag uncertainty explicitly with "likely", "subject to counsel", or `[ ]` open questions rather than guessing.
- Match the existing voice: disclaimer blockquote at the top of legal/tax files, tables for facts, prose for reasoning, `- [ ]` checklists, Spanish legal terms preserved (`S.A. de C.V.`, `Sociedad Anónima`, `Régimen de Condominio`, `Zona Marítimo Terrestre`).
- See AGENTS.md "Don'ts" for hard bans (no real names/RFCs/account numbers, no specific firm endorsements, no promised tax outcomes, no merged Malta+CR narratives).

## Commit etiquette

- Stage explicitly: `git add docs/<path>/<file>.md`. Never `git add -A` here — the working tree is small enough that explicit staging is faster than reviewing a wildcard.
- Run `git diff --cached --stat` in the same bash block as `git commit`, gated on the expected file count. (Inherited QIE rule, applies even to this small repo because other Claude sessions may be in worktrees.)
- Conventional commit prefix: `docs(malta): ...`, `docs(cr): ...`, `chore: ...`. Match the seed commit's plain-prose style if unsure.

## Skill / harness false positives to ignore

- The `vercel-plugin:bootstrap` skill auto-suggests when reading `README.md`. Ignore it — there is no Vercel project here, no Next.js, no env vars, no deploy. Same for any other Vercel/Next/Supabase/Stripe skill that auto-loads.
- The `vercel-plugin:nextjs` and similar React/build-tool skills are not applicable. Markdown only.
- If a skill insists on writing config files, decline. This repo's tooling is `git` and a markdown editor.

## Slash commands

QIE master agents (`/bmad-agent-*`, `/quinn`) are available via the `_qie` symlink at the QIE root. None are NUMA-specific.
