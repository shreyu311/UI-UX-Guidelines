# 3 · UI/UX system plan — process & validation (SSOT)

<aside>
**Executive entry point:** [UI/UX System Proposal Plan](../../CUSTOMIZATION.md) — presents the full program in one place; this page is the **process detail** layer.

</aside>

## What this is

**Single source of truth** for how UI/UX requirements are **defined**, **mocked**, and **validated** across **all [YOUR_COMPANY_NAME] projects**. Executable rules in repo live in **`design.md`**; this page + the linked repo doc together form the full system.

<aside>
**Canonical file (engineering / agents):** `UI-UX-SYSTEM-PLAN.md` in the **Design** workspace root — keep Notion and repo in sync when this plan changes.

</aside>

## How truth stacks

1. **This system plan** — process, requirement categories, mock workflow, validation gates, exceptions philosophy.
2. **Org `design.md`** — ShadCN-first, tokens, WCAG target, mandatory **Loading / Empty / Error / Success**, PR snippet: [UI/UX guidelines hub](UI%20UX%20guidelines%2020be6c5f913d4f53ac0e76eb5e904eef.md)
3. **Project PRD + UI spec + mocks** — what each product builds; must trace to requirements.
4. **Exceptions log** — approved deviations only: [4 · UI/UX exceptions log — approved deviations](4%20%C2%B7%20UI%20UX%20exceptions%20log%20%E2%80%94%20approved%20deviations%2042cc3261a0d84faaaf6420c0061d7f71.md)

## Requirement categories (use for every feature)

Spec each scope under: **(1)** users & tasks **(2)** layout & IA **(3)** visual tokens **(4)** components/patterns **(5)** interaction & states **(6)** accessibility & i18n **(7)** data/edge cases. This schema is how mocks and QA stay comparable across projects.

## Mockups & prototypes

**Stakeholder / exec bar:** packages need **on-page visuals** (screenshots, embeds, or an obvious interactive link), not prose alone. See [CUSTOMIZATION.md](../../CUSTOMIZATION.md) for adapting this template.

**Required** for new surfaces, major layout/nav changes, or exec-facing review. Accepted: wireframes, Figma/Stitch/high-fi, clickable proto, annotated Notion/Markdown spec. **Rule:** mocks **link to requirement anchors** (ticket IDs or doc sections).

**Tools:** Figma, Stitch, Cursor + `design.md`, static HTML previews — pick per project; **outputs** must be reviewable and tied to specs.

## Validation gates

- **Before build:** §4 categories filled; mock covers happy + **empty** + **error** minimum.
- **Before merge:** org **PR snippet** completed (tokens, ShadCN, states, a11y).
- **Before release:** matches approved mock within tolerance; no **silent** deviations.

## Exceptions

Log **what / why / approver / evidence**; avoid permanent one-offs — recurring gaps update the standard.

## Project onboarding (all products)

1. Link org `design.md`.
2. Maintain project UI spec + mocks.
3. Name UI/UX point person for coherence.
4. Surface data/legal dependencies early.

## Governance & packaging

- Program overview: [README.md](../../README.md)
- Customization guide: [CUSTOMIZATION.md](../../CUSTOMIZATION.md)

## RACI (short)

**Standard owners** maintain plan + `design.md`. **PM/product** owns requirements + mocks. **Eng** owns implementation + PR checklist. **Approver** signs exceptions.

## Version

**v1.1** · 2026-04-03 — stakeholder-visible proof (exec bar) aligned with hub + CTO package; see repo `UI-UX-SYSTEM-PLAN.md` §1.1. Next review: quarterly or after major stack change.

---

*Detail, checklists, and tables: see `UI-UX-SYSTEM-PLAN.md` in the Design repo.*