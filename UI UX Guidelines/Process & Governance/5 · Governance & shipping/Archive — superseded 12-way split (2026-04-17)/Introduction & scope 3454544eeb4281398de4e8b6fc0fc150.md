# Introduction & scope

> **Former location:** Part I — § 1 in the CTO hub. This page is the **entry** for purpose, scope, and how this standard binds engineering.
> 

## Purpose

This standard is the single source of truth for UI/UX decisions when designing or implementing **aosenuma** product experiences. It defines brand-aligned constraints and a repeatable workflow for consistent UI using **ShadCN + Tailwind**.

## Scope (what this standard governs)

- Screen and component UX patterns (layout, hierarchy, interaction)
- Visual system (colors, typography, spacing, radii)
- Product copy tone for UI messaging
- Required UI states and accessibility baseline
- Implementation constraints (ShadCN-first, token-driven styling)

## What this is / is not (framework alignment)

- **It is:** SSOT for tokens, components, required states, accessibility, and handoff expectations across engineering.
- **It is not:** A project roadmap, research archive, or replacement for curated external mood boards — those **inform** but do not override this doc.

## Binding standard (summary)

- **Stack:** ShadCN-first, Tailwind tokens; no one-off colors unless exception-approved (`docs/design-exceptions.md`).
- **Documentation shape:** Inventory **all UI elements** → **categories** → **specific rules per category** (not only a global type scale). Dense surfaces may differ from marketing — document per context in Figma.
- **Proof format:** Prefer **visual documentation in Figma** (palette + gradients on real components, states, spacing callouts). Text-only specs are not enough for stakeholder sign-off on look-and-feel.

## Repo SSOT

Projects pin the current standard at `docs/design.md` (or repo-root `design.md`). Exceptions are logged in `docs/design-exceptions.md`.

## Owner

- **UI/UX Standards Owner:** Shreyas Shirke (per Governance).