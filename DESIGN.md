# DESIGN.md — agent projection (Stitch / Claude / generators)

**Not org-wide SSOT:** any `DESIGN.md` nested under **`UI UX Guidelines/Projects/`** describes **pilots only** — see [`UI UX Guidelines/Projects/README.md`](UI%20UX%20Guidelines/Projects/README.md).

**Full source of truth:** [`UI UX Guidelines/UI UX guidelines 20be6c5f913d4f53ac0e76eb5e904eef.md`](UI%20UX%20Guidelines/UI%20UX%20guidelines%2020be6c5f913d4f53ac0e76eb5e904eef.md). This file at repo root is a **short, generator-friendly** projection; refresh it when `globals.css` (or your shipped theme) or hub tables change.

## Non-negotiables

- **Tokens first:** no orphan hex in shipped UI; map to semantic roles.
- **Components first:** documented variants (e.g. ShadCN-style primary / secondary / ghost / destructive) — do not fork without a logged exception.
- **States:** loading, empty, error, and success on meaningful surfaces; controls follow the **Components & patterns** matrix.
- **Gradient:** only **135deg** **#164F5B → #208692** for the approved primary gradient.
- **Branding:** Aosenuma branding by default on prototypes and exports (logo, palette, type, metadata) unless an exception is filed per governance.

## Semantic palette (compact)

| Role | Default | Notes |
| --- | --- | --- |
| Primary teal | **#208692** | CTAs, links; hover/deep **#164F5B** |
| Sage wash | **#E5EADF** | Ghost/secondary hover wash |
| Destructive | **#DC2626** / hover **#B91C1C** | Never for marketing emphasis |
| Success | **#16A34A** | Confirmations |
| Warning | **#F59E0B** | Non-blocking risk |
| Info | **#3B82F6** | Informational only |
| Disabled | **#D1D5DB** fill · **#9CA3AF** text | |

## Layout

- **8pt grid**; common spacing **4 / 8 / 16 / 24 / 32 / 48 / 64**.
- **Radius baseline:** **12px** (`--radius` where applicable).
- **Touch targets:** ≥ **44×44** px where interactive.
- **Button heights** (reference): **48 / 40 / 32**; large CTA horizontal padding **32px** per side.

## ShadCN-style mapping (at-a-glance)

| Label | Variant | Default fill | Hover |
| --- | --- | --- | --- |
| Contained | primary | **#208692** | **#164F5B** |
| Outlined | secondary | border muted, deep text | wash **#E5EADF** |
| Text | ghost | transparent | wash **#E5EADF** |
| Destructive | destructive | **#DC2626** | **#B91C1C** |

## Figma

Mirror **token names** and component structure to the code library; semantic variables should match the hub and implementation.

## Reject instructions

If generated UI uses raw hex outside the table, generic blue primaries, decorative gradients other than the approved one, or **semantic red** for non-destructive emphasis → **regenerate** against the hub and **Brand, layout & tokens** / **Components & patterns** chapters.

## Deep links (this repo)

- Components & patterns: [`UI UX Guidelines/Standards/4 · Components & patterns 3454544eeb4281479040ce5bd99406c7.md`](UI%20UX%20Guidelines/Standards/4%20%C2%B7%20Components%20%26%20patterns%203454544eeb4281479040ce5bd99406c7.md)
- Brand & tokens: [`UI UX Guidelines/Standards/2 · Brand, layout & tokens 3454544eeb4281ce92bbf7eb90df3835.md`](UI%20UX%20Guidelines/Standards/2%20%C2%B7%20Brand,%20layout%20%26%20tokens%203454544eeb4281ce92bbf7eb90df3835.md)
- Consolidation map: [`UI UX Guidelines/Workflow & Tooling/9 · Consolidation map — Notion · Repo · Stitch · F 34a4544eeb4281b5a45bd1d1321b52bf.md`](UI%20UX%20Guidelines/Workflow%20%26%20Tooling/9%20%C2%B7%20Consolidation%20map%20%E2%80%94%20Notion%20%C2%B7%20Repo%20%C2%B7%20Stitch%20%C2%B7%20F%2034a4544eeb4281b5a45bd1d1321b52bf.md)
