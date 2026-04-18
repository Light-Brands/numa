# NUMA — Agent Operating Rules

Canonical rules for any agent (Claude, human, or otherwise) working in this repo. Read this before editing anything.

## What this is

NUMA is a **research-and-planning vault** for two parallel cross-border deals owned by a single Mexican-resident principal:

1. **Malta loan repayment** (`docs/01-malta-repayment/`) — receipt of a $350K convertible-note repayment from a Malta entity to Mexico, with a 2-week execution window and a broken paper trail (the originating Mexican S.A. de C.V. and personal account are both inactive). Goal: classify as Scenario A (return of principal) cleanly enough to survive SAT scrutiny.
2. **Costa Rica master development** (`docs/02-costa-rica-development/`) — 111-hectare Santa Teresa land deal, $5.5M acquisition (10% cash / 90% landowner equity), $1M seed across two investor groups, 20-plot subdivision targeting ~$63M gross revenue. Multi-jurisdiction investors (US, EU, MX, plus "other").

There is no application. There is no build. There is no website. **This repo is markdown only.** Its purpose is to make the deals legible to qualified counsel and to the principal himself.

## Stack

- Markdown. That's it.
- No `package.json`, no `pyproject.toml`, no Cargo, no Vercel, no CI. Do not invent any.
- GitHub remote: `git@github.com:Light-Brands/numa.git`. Single `main` branch upstream.

## Where things live

```
README.md                                    Public-facing index of the two projects
docs/
  01-malta-repayment/
    situation-analysis.md                    Facts, entities, timeline, doc checklist
    tax-strategy.md                          Scenarios A/B/C, MX-MT treaty, SAT compliance
    banking-strategy.md                      Account selection, AML, wire prep
    action-plan.md                           14-day execution checklist
  02-costa-rica-development/
    project-overview.md                      Executive summary + capital stack
    land-acquisition/acquisition-structure.md   Purchase terms, Maritime Zone risk, DD checklist
    master-plan/subdivision-strategy.md         20-plot subdivision, condominium regime, permitting
    legal-structure/entity-design.md            Options A/B/C; Option B (Holdings + Tierras + Desarrollo) is recommended
    financial-structure/seed-capital.md         Seed sources, capital stack, projections
    investor-relations/investor-framework.md    Two investor groups, protections, securities-law analysis
research/                                    Empty. Drop primary-source research here (statutes, treaty text, market comps).
templates/                                   Empty. Drop reusable templates here when patterns emerge across deals.
```

## Current focus (per recent commits)

Single commit on `main` (`5eb8eda` — "Initial NUMA project"). The repo was seeded Feb 2026 and `project-overview.md` was last touched 2026-04-18. Next likely work: filling out `research/` and `templates/`, expanding `seed-capital.md` (TBD line items), and resolving open questions called out in `acquisition-structure.md` (Maritime Zone status, landowner equity %, sunset trigger for the 10-hectare guarantee).

A `claude/doctrine-bootstrap` branch on origin contains a generic QIE doctrine — this branch (`claude/app-aware-doctrine`) replaces it with project-specific rules.

## Conventions (real patterns observed)

- **Every legal/tax file opens with a `> **Disclaimer**:` blockquote.** Match the existing wording. These docs are research frameworks for qualified counsel, not advice. Do not write anything that reads as legal advice.
- **Tables for facts, prose for reasoning.** The existing files use markdown tables for entities, capital stacks, jurisdictions, and timelines; prose for "why this option" narrative.
- **Checklists are `- [ ]`** (unchecked). Items get checked when actually completed in the real world, not when documented.
- **Entity names appear in code-style or bold.** `S.A. de C.V.`, `NUMA Holdings S.A.`, `Sociedad Anónima`. Spanish legal terms stay in Spanish (italicize on first use only if non-obvious).
- **Money in USD unless specified.** When MXN or CRC matters, name the currency explicitly.
- **Costa Rica entity names follow the pattern `NUMA <Spanish noun> S.A.`** — `NUMA Holdings`, `NUMA Tierras`, `NUMA Desarrollo`, `NUMA Ventas`. Stay consistent if you add more.
- **Section numbering matches the directory prefix** (`01-malta-repayment`, `02-costa-rica-development`). New top-level project areas should continue the numbering: `03-...`.

## Gotchas (only learnable by reading the code)

- **The Malta repayment timeline is real and short.** `action-plan.md` is a 14-day clock. If you're editing tax-strategy.md, the principal may be making decisions against your text within days. Be precise; flag uncertainty explicitly rather than soft-pedaling.
- **Scenario A vs B vs C in `tax-strategy.md` is the load-bearing decision.** Scenario A (pure principal return, non-taxable) is the target. Anything you write that muddies the principal-vs-interest distinction makes the Scenario A position weaker. Don't.
- **The original Mexican S.A. de C.V. and personal account are both inactive.** This is the central evidentiary problem. Any new strategy doc must address how it survives that constraint, not assume the records exist.
- **Santa Teresa is coastal.** Maritime Zone (Zona Marítimo Terrestre) analysis is mandatory before any acquisition assumption holds. The 200m-from-high-tide rule controls what foreigners can own. Flagged but unresolved in `acquisition-structure.md`.
- **The 10-hectare guarantee implies a per-hectare valuation of $55K vs the $49.5K blended price** — meaning the security is slightly over-collateralized. Don't accidentally edit one number without re-checking the other.
- **Capital stack rounding:** `seed-capital.md` shows the down payment as a *subset* of the $1M seed (negative entry), not as a separate stack layer. Total initial capital is $6M, not $7M. Easy to break.
- **Investor "Group 2" is a placeholder.** "TBD structure" appears in multiple files. Don't infer a fund structure that hasn't been decided.
- **Three jurisdictions per project, minimum.** Malta deal: MX + MT + CR (the original obligor). CR deal: CR + US + EU + MX. Tax/legal claims that ignore any leg are wrong.

## Don'ts

- **Don't add a `package.json`, lockfile, build config, or Vercel config.** This is not a deployable project; tooling will only confuse future agents.
- **Don't write in the principal's voice or counsel's voice.** Write as a researcher producing material *for* counsel and the principal.
- **Don't recommend a specific bank, attorney, or firm by name as "the choice."** The existing docs list options (BBVA, Banorte, Citibanamex) without endorsing one. Maintain that posture.
- **Don't put real names, RFCs, account numbers, passport numbers, or counterparty identifiers anywhere in the repo.** The current docs use generic descriptors ("the individual", "the Malta company", "the landowner"). Keep it that way. If you need an identifier, invent a placeholder and call it out.
- **Don't promise tax outcomes.** Use "likely", "subject to", "pending counsel review". Never "will be tax-free".
- **Don't merge the Malta and Costa Rica narratives.** They share the principal but are separate deals with separate counsel and separate timelines. Keep their docs strictly siloed.

## Secrets

There are no secrets in this repo and there should never be. No `.env` files, no credentials, no API keys, no scans of IDs or bank statements. If you ever find yourself about to commit a real account number, RFC, passport scan, signed agreement, or attorney-client correspondence — stop. Those belong in `legal-vault/numa/` at the QIE root, not here. This repo is the *thinking*, not the *evidence*.
