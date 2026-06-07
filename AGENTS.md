# Agent instructions (Claude, Cursor, CI bots)

Use this file so automated tools know **where the binding UI/UX rules live** in this repository.

## Authority order

1. **BRANDBOOK.md** — company brand identity (colors, fonts, logo, voice). **Customize this first.**
2. **Hub** — [`UI UX Guidelines/UI UX guidelines`](UI%20UX%20Guidelines/UI%20UX%20guidelines%2020be6c5f913d4f53ac0e76eb5e904eef.md) (semantic color, principles, branding pointers).
3. **Standards chapters** — under `UI UX Guidelines/Standards/`.
4. **Process & governance** — under `UI UX Guidelines/Process & Governance/`.
5. **Machine-readable excerpt** — [`DESIGN.md`](DESIGN.md). If `DESIGN.md` and the hub disagree, **the hub wins**.

## Tool-specific

- **Figma:** Component and variable naming should align with token names in `BRANDBOOK.md`. Do not invent off-palette accents.
- **Claude / Cursor:** Read [`Workflow & Tooling/6 · Workflow`](UI%20UX%20Guidelines/Workflow%20%26%20Tooling/6%20%C2%B7%20Workflow%20%E2%80%94%20Claude%20Design%20%E2%86%92%20Claude%20Code%203474544eeb4281568702e4dd71f825a6.md). Use tokens from `BRANDBOOK.md` — never ship generic Material/blue defaults.
- **Google Stitch / codegen:** Treat [`DESIGN.md`](DESIGN.md) as the import surface; expand from the hub for full rules.

## Customization

Any team forking this repo should:
1. Edit [`BRANDBOOK.md`](BRANDBOOK.md) with their brand values.
2. Sync [`DESIGN.md`](DESIGN.md) with resolved hex values.
3. Update [`.github/CODEOWNERS`](.github/CODEOWNERS) with their team.

See [`CUSTOMIZATION.md`](CUSTOMIZATION.md) for the full guide.

## Reject / fix before handoff

Reject outputs that use **orphan hex** instead of semantic tokens, **off-grid spacing**, wrong **semantic red** usage, or **unbranded** external-facing artifacts. Enforce **loading / empty / error / success** states where required.
