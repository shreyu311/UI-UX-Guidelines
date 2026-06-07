# Contributing to UI/UX Guidelines

Thank you for helping improve this open UI/UX guidelines template.

## What is binding (single source ladder)

Resolve conflicts using this order:

1. **BRANDBOOK.md** — your company's brand identity (colors, fonts, logo, voice).
2. **Hub** — [`UI UX Guidelines/UI UX guidelines`](UI%20UX%20Guidelines/UI%20UX%20guidelines%2020be6c5f913d4f53ac0e76eb5e904eef.md).
3. **Standards chapters** — [`UI UX Guidelines/Standards/`](UI%20UX%20Guidelines/Standards/).
4. **Process & Governance** — exceptions, governance, playbooks.
5. **Root [`DESIGN.md`](DESIGN.md)** — agent/codegen projection only; never overrides the hub.

## Customizing for your company

See [`CUSTOMIZATION.md`](CUSTOMIZATION.md). Keep brand-specific values in your fork — contribute structural improvements back via PR.

## Pull request checklist

- [ ] Identify which tier your change touches (BRANDBOOK / hub / Standards / DESIGN.md).
- [ ] If touching semantic tokens, update [`DESIGN.md`](DESIGN.md) in the same PR.
- [ ] Run a quick Markdown preview for broken relative links.

## CODEOWNERS

Configure [`.github/CODEOWNERS`](.github/CODEOWNERS) with your `@org/team-slug` or `@username`.
