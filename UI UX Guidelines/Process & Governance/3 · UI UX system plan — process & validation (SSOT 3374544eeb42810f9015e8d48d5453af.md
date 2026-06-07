# 3 · UI/UX system plan — process & validation

## What this is

Template for how UI/UX requirements are **defined**, **mocked**, and **validated** across projects. Executable rules live in **`design.md`** (or repo root `DESIGN.md`); this page describes the process layer.

## How truth stacks

1. **BRANDBOOK.md** — your company's brand identity
2. **This hub + Standards** — binding UI/UX rules
3. **Project PRD + UI spec + mocks** — what each product builds
4. **Exceptions log** — [approved deviations](4%20%C2%B7%20UI%20UX%20exceptions%20log%20%E2%80%94%20approved%20deviations%2042cc3261a0d84faaaf6420c0061d7f71.md)

## Requirement categories (use for every feature)

Spec each scope under: **(1)** users & tasks **(2)** layout & IA **(3)** visual tokens **(4)** components/patterns **(5)** interaction & states **(6)** accessibility & i18n **(7)** data/edge cases.

## Mockups & prototypes

Packages need **on-page visuals** (screenshots, embeds, or an interactive link), not prose alone. Accepted: wireframes, Figma/Stitch/high-fi, clickable proto, annotated spec.

**Tools:** Figma, Stitch, Cursor + `design.md`, static HTML previews — pick per project.

## Validation gates

- **Before build:** requirement categories filled; mock covers happy + empty + error minimum
- **Before merge:** PR checklist completed (tokens, components, states, a11y)
- **Before release:** matches approved mock; no silent deviations

## Exceptions

Log **what / why / approver / evidence** in the exceptions log. Avoid permanent one-offs — recurring gaps update the standard.

## Project onboarding

1. Link org `design.md` or `DESIGN.md`
2. Maintain project UI spec + mocks in a `projects/` folder (see [CUSTOMIZATION.md](../../CUSTOMIZATION.md))
3. Name a UI/UX point person
4. Surface data/legal dependencies early
