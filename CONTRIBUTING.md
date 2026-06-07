# Contributing to UI/UX Guidelines

Thank you for helping keep the design system coherent across products and tooling.

## What is binding (single source ladder)

Resolve conflicts using this order:

1. **Hub:** [`UI UX Guidelines/UI UX guidelines 20be6c5f913d4f53ac0e76eb5e904eef.md`](UI%20UX%20Guidelines/UI%20UX%20guidelines%2020be6c5f913d4f53ac0e76eb5e904eef.md) — semantic color, branding principles, pointers to numbered chapters.
2. **Standards chapters** — [`UI UX Guidelines/Standards/`](UI%20UX%20Guidelines/Standards/) (`1 · Scope` … `4 · Components`, tokens, brand assets). **These are binding for shipped UI semantics** when cited by the hub.
3. **`UI UX Guidelines/Process & Governance/`** — exceptions logs, governance, mandated reporting/playbooks.
4. **Root [`DESIGN.md`](DESIGN.md)** — Stitch/agent projection only; never overrides the hub. **Refresh [`DESIGN.md`](DESIGN.md) whenever semantic tokens change in code or hub tables** (same rhythm as the [consolidation map](UI%20UX%20Guidelines/Workflow%20%26%20Tooling/9%20%C2%B7%20Consolidation%20map%20%E2%80%94%20Notion%20%C2%B7%20Repo%20%C2%B7%20Stitch%20%C2%B7%20F%2034a4544eeb4281b5a45bd1d1321b52bf.md)).

### Planning folder vs Standards

[`UI UX Guidelines/Planning & Meetings/Company UI UX standards/`](UI%20UX%20Guidelines/Planning%20%26%20Meetings/Company%20UI%20UX%20standards/) contains **templates, onboarding, and program docs** migrated from workspace planning workflows. Treat it as **onboarding / governance scaffolding**. If wording conflicts with **`Standards/`** + the hub, **update Planning copy to match Standards** rather than inventing competing rules.

## What is non-binding (`Projects/`)

Everything under **`UI UX Guidelines/Projects/`** is **pilot**, **experiment**, **compliance note**, **prototype artifact**, **or Stitch/codegen output**. **Never** cite a project-local `DESIGN.md` as the organizational default—the **hub + root `DESIGN.md`** are. See [`UI UX Guidelines/Projects/README.md`](UI%20UX%20Guidelines/Projects/README.md).

## Links to Notion and other canonical sources

Several pages still reference **Notion URLs** where that workspace remains canonical for stakeholder history, embeds, or live collaboration. Prefer **duplicate critical rules into this repo** when you adopt GitHub-as-SSOT; otherwise keep links working and annotate in the PR if URLs move.

## Pull request checklist

- [ ] Identify which **tier** above your change touches (hub / Standards / DESIGN.md / pilots only).
- [ ] If touching **semantic tokens or palettes**, confirm **[`DESIGN.md`](DESIGN.md)** is updated in the **same PR** (or explicitly note why not).
- [ ] If adding a pilot, add a banner at top of artifact (see Prediction Market pilot) and **`Projects/README`** if it is new pattern.
- [ ] Run a quick Markdown preview for broken relative links changed in-scope.

## CODEOWNERS

After clone, uncomment and configure [`.github/CODEOWNERS`](.github/CODEOWNERS) with real `@org/team-slug` or `@username` so reviews route correctly.
