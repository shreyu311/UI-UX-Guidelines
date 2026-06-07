# DESIGN.md — agent projection (AI codegen / generators)

**Brand source of truth:** [`BRANDBOOK.md`](BRANDBOOK.md) — replace placeholders there first, then sync this file.

**Full UI/UX rules:** [`UI UX Guidelines/UI UX guidelines`](UI%20UX%20Guidelines/UI%20UX%20guidelines%2020be6c5f913d4f53ac0e76eb5e904eef.md). This file is a **short, generator-friendly** projection.

## Non-negotiables

- **Tokens first:** no orphan hex in shipped UI; map to semantic roles from `BRANDBOOK.md`.
- **Components first:** documented variants (primary / secondary / ghost / destructive) — do not fork without a logged exception.
- **States:** loading, empty, error, and success on meaningful surfaces.
- **Gradient:** only your approved primary gradient from `BRANDBOOK.md` — no decorative one-offs.
- **Branding:** your company branding by default on prototypes and exports (logo, palette, type) unless an exception is filed.

## Semantic palette (compact)

> Replace hex values with your `BRANDBOOK.md` tokens.

| Role | Token | Default | Notes |
| --- | --- | --- | --- |
| Primary | `primary` | `[YOUR_PRIMARY]` | CTAs, links |
| Primary dark | `primary-dark` | `[YOUR_PRIMARY_DARK]` | Hover, nav, headers |
| Accent wash | `surface-wash` | `[YOUR_SURFACE_WASH]` | Ghost/secondary hover |
| Destructive | `destructive` | `#DC2626` / hover `#B91C1C` | Never for marketing |
| Success | `success` | `#16A34A` | Confirmations |
| Warning | `warning` | `#F59E0B` | Non-blocking risk |
| Info | `info` | `#3B82F6` | Informational only |
| Disabled | `disabled-fill` / `disabled-text` | `#D1D5DB` / `#9CA3AF` | |

## Layout

- **8pt grid**; spacing scale **4 / 8 / 16 / 24 / 32 / 48 / 64**.
- **Radius baseline:** **12px**.
- **Touch targets:** ≥ **44×44** px.
- **Button heights:** **48 / 40 / 32** px.

## Component mapping (at-a-glance)

| Label | Variant | Default fill | Hover |
| --- | --- | --- | --- |
| Contained | primary | `[YOUR_PRIMARY]` | `[YOUR_PRIMARY_DARK]` |
| Outlined | secondary | border muted | `[YOUR_SURFACE_WASH]` |
| Text | ghost | transparent | `[YOUR_SURFACE_WASH]` |
| Destructive | destructive | `#DC2626` | `#B91C1C` |

## Figma

Mirror **token names** and component structure to the code library; semantic variables should match `BRANDBOOK.md` and implementation.

## Reject instructions

Regenerate if output uses raw hex outside the token table, generic off-brand primaries, unapproved gradients, or semantic red for non-destructive emphasis.

## Deep links

- Components: [`Standards/4 · Components & patterns`](UI%20UX%20Guidelines/Standards/4%20%C2%B7%20Components%20%26%20patterns%203454544eeb4281479040ce5bd99406c7.md)
- Brand & tokens: [`Standards/2 · Brand, layout & tokens`](UI%20UX%20Guidelines/Standards/2%20%C2%B7%20Brand,%20layout%20%26%20tokens%203454544eeb4281ce92bbf7eb90df3835.md)
- Your brandbook: [`BRANDBOOK.md`](BRANDBOOK.md)
