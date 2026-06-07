# Agent instructions (Claude, Cursor, CI bots)

Use this file so automated tools know **where the binding UI/UX rules live** in this repository.

## Authority order

1. **Hub** — [`UI UX Guidelines/UI UX guidelines 20be6c5f913d4f53ac0e76eb5e904eef.md`](UI%20UX%20Guidelines/UI%20UX%20guidelines%2020be6c5f913d4f53ac0e76eb5e904eef.md) (semantic color, principles, branding, pointers to chapters).
2. **Standards chapters** — under `UI UX Guidelines/Standards/` (scope, brand/tokens, style card, components, governance, brand assets).
3. **Process & governance** — under `UI UX Guidelines/Process & Governance/`.
4. **Machine-readable excerpt** — [`DESIGN.md`](DESIGN.md) at repo root (for Stitch / narrow context windows). If `DESIGN.md` and the hub disagree, **the hub wins**; update `DESIGN.md`.

**Do not treat `UI UX Guidelines/Projects/**` as binding** unless a doc explicitly records promotion into `Standards/`. Pilot `DESIGN.md` files describe **product-specific experiments** — see [`UI UX Guidelines/Projects/README.md`](UI%20UX%20Guidelines/Projects/README.md).

## Tool-specific

- **Figma:** Component and variable naming should align with token names and the **Components & patterns** chapter. Visual proof and embeds are referenced from the hub; do not invent off-palette accents.
- **Claude Design → Claude Code:** Read [`UI UX Guidelines/Workflow & Tooling/6 · Workflow — Claude Design → Claude Code 3474544eeb4281568702e4dd71f825a6.md`](UI%20UX%20Guidelines/Workflow%20%26%20Tooling/6%20%C2%B7%20Workflow%20%E2%80%94%20Claude%20Design%20%E2%86%92%20Claude%20Code%203474544eeb4281568702e4dd71f825a6.md). Do not ship generic blue/Material defaults; match onboarded tokens (primary teal **#208692**, deep **#164F5B**, etc.).
- **Google Stitch:** Treat [`DESIGN.md`](DESIGN.md) as the import surface; expand from the hub for full rules.

## Consolidation (four surfaces)

[`UI UX Guidelines/Workflow & Tooling/9 · Consolidation map — Notion · Repo · Stitch · Figma 34a4544eeb4281b5a45bd1d1321b52bf.md`](UI%20UX%20Guidelines/Workflow%20%26%20Tooling/9%20%C2%B7%20Consolidation%20map%20%E2%80%94%20Notion%20%C2%B7%20Repo%20%C2%B7%20Stitch%20%C2%B7%20F%2034a4544eeb4281b5a45bd1d1321b52bf.md) explains how Notion, repo, `DESIGN.md`, and Figma relate—**one design system, multiple surfaces**.

## Reject / fix before handoff

Reject outputs that use **orphan hex** instead of semantic tokens, **off-grid spacing** outside the documented scale, wrong **semantic red** usage, or **unbranded** external-facing artifacts when branding is required. Enforce **loading / empty / error / success** states where the components chapter requires them.
