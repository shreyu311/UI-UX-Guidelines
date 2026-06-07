# 1 · Scope & principles

## Purpose & scope

This document is the single source of truth for **aosenuma** product UI: layout, hierarchy, interaction, visual system, in-product language, required states, and accessibility. Implementation uses **ShadCN + Tailwind** with tokens from **`globals.css`**.

### Scope

- Screen and component UX patterns
- Color, typography, spacing, radii, elevation
- In-product copy tone
- Required UI states and accessibility expectations
- ShadCN-first, token-driven styling

### Brand palette snapshot

Canonical product colors (see [2 · Brand, layout & tokens](2%20%C2%B7%20Brand,%20layout%20&%20tokens%203454544eeb4281ce92bbf7eb90df3835.md) for usage, gradients, and semantic rules).

| Role | HEX | Token (code) |
| --- | --- | --- |
| Primary / focus | **#208692** | `--primary`, `--ring` |
| Deep / nav chrome | **#164F5B** | `deep` (Figma) / paired with accessible text |
| Accent (highlight only) | **#D4D970** | `--accent` |
| Page background | **#F4F5F0** | `--background` |
| Default text | **#26272A** | `--foreground` |
| Border / muted fill | **#CFD0BF** | `--border`, `--muted` |
| Muted text | **#527779** | `--muted-foreground` |
| Secondary wash | **#C7D8D0** | `--secondary` |
| Success / warning / error (chips & states) | **#16A34A** / **#F59E0B** / **#DC2626** | map to semantic components in **4 · Components** |

### Visual swatches (Figma / PNG)

Scope page uses **tables** for canonical HEX. For **Apr 14 visual proof** (gradients + hover on real components), use **Figma embeds** or **PNGs** in [2 · Brand, layout & tokens](2%20%C2%B7%20Brand,%20layout%20&%20tokens%203454544eeb4281ce92bbf7eb90df3835.md) and [3 · Style Card for UI/UX](3%20%C2%B7%20Style%20Card%20for%20UI%20UX%203454544eeb428013a31df04ad5caa2e2.md) — avoid generated remote tiles here.

### What this is / is not

- **It is** the binding reference for design and engineering.
- **It is not** a delivery roadmap, research repository, or a substitute for brand legal rules — external inspiration **does not** override these guidelines.

### Working agreements

- **Tokens first:** no one-off colors unless approved and logged in `docs/design-exceptions.md`.
- **Inventory → categories → rules:** every recurring element gets a named pattern with states (see inventory table below).
- **Visual proof in Figma:** show palette, gradients, spacing, and motion on **real components**.

### UI element inventory (categories → guidelines)

Single map from UI domains to the living spec. If a row points to a section that is still thin for your product, **extend the guidelines before shipping** net-new UI in that area.

| Category | Elements (examples) | Guidelines location |
| --- | --- | --- |
| Color & layout foundations | Palette, gradients, grid, radius, elevation | [2 · Brand, layout & tokens](2%20%C2%B7%20Brand,%20layout%20&%20tokens%203454544eeb4281ce92bbf7eb90df3835.md) |
| Actions | Buttons, icon buttons, split buttons, button groups, menus | [4 · Components & patterns](4%20%C2%B7%20Components%20&%20patterns%203454544eeb4281479040ce5bd99406c7.md) — Buttons |
| Forms & selection | Text inputs, text areas, selects, checkboxes, radios, switches, date/time, file upload | [4 · Components & patterns](4%20%C2%B7%20Components%20&%20patterns%203454544eeb4281479040ce5bd99406c7.md) — Controls & inputs |
| Feedback | Alerts, toasts, banners, validation, progress, skeletons | [2 · Brand, layout & tokens](2%20%C2%B7%20Brand,%20layout%20&%20tokens%203454544eeb4281ce92bbf7eb90df3835.md) (semantics) + [4 · Components & patterns](4%20%C2%B7%20Components%20&%20patterns%203454544eeb4281479040ce5bd99406c7.md) (Required states, Notifications) |
| Navigation & shell | Primary nav, tabs, breadcrumbs, page headers, app bars | [4 · Components & patterns](4%20%C2%B7%20Components%20&%20patterns%203454544eeb4281479040ce5bd99406c7.md) — **Navigation & shell** |
| Data display | Tables, cards, lists, KPI tiles, charts/maps in product | [4 · Components & patterns](4%20%C2%B7%20Components%20&%20patterns%203454544eeb4281479040ce5bd99406c7.md) — **Data display & visualization** |
| Overlays | Modals, drawers, popovers, command palettes | [4 · Components & patterns](4%20%C2%B7%20Components%20&%20patterns%203454544eeb4281479040ce5bd99406c7.md)  • [2 · Brand, layout & tokens](2%20%C2%B7%20Brand,%20layout%20&%20tokens%203454544eeb4281ce92bbf7eb90df3835.md) (shadows, radius) |
| Content & UX writing | Microcopy, errors, empty states, imagery guidance | [4 · Components & patterns](4%20%C2%B7%20Components%20&%20patterns%203454544eeb4281479040ce5bd99406c7.md) — Content & accessibility |
| Style previews | Style cards, posters, internal one-pagers | [3 · Style Card for UI/UX](3%20%C2%B7%20Style%20Card%20for%20UI%20UX%203454544eeb428013a31df04ad5caa2e2.md) |

### Where to look next

- **Visual system + tokens:** [2 · Brand, layout & tokens](2%20%C2%B7%20Brand,%20layout%20&%20tokens%203454544eeb4281ce92bbf7eb90df3835.md)
- **Components, patterns, content, accessibility:** [4 · Components & patterns](4%20%C2%B7%20Components%20&%20patterns%203454544eeb4281479040ce5bd99406c7.md)
- **Style card / poster:** [3 · Style Card for UI/UX](3%20%C2%B7%20Style%20Card%20for%20UI%20UX%203454544eeb428013a31df04ad5caa2e2.md)
- **Ownership, shipping checklist, exceptions:** [5 · Governance & shipping](../Process%20&%20Governance/5%20%C2%B7%20Governance%20&%20shipping%203454544eeb4281808c68e067d0b6a0f7.md)

### Repo

- Canonical text spec: `docs/design.md` or repo-root `design.md`
- Exceptions: `docs/design-exceptions.md`

### Standards owner

- Shreyas Shirke

---

## Principles

- **Consistency over novelty** — reuse approved patterns before inventing new ones.
- **Clarity first** — hierarchy, labels, and whitespace reduce cognitive load.
- **Accessible by default** — contrast, keyboard support, visible focus.
- **States are mandatory** — loading, empty, error, success.

### When principles conflict

Accessibility and **recoverability** win over novelty.

### Tooling expectations

- Keep tokens and patterns **machine-readable** for handoff and implementation.
- Prefer **Figma** with semantic variables aligned to code.
- Capture **visual acceptance criteria** whenever interaction quality matters.

---

## Review checklist (pre-merge)

- [ ]  ShadCN components (or documented fork)
- [ ]  Token-driven styling (no orphan hex)
- [ ]  Loading · empty · error · success covered
- [ ]  Keyboard, focus, and semantics verified
- [ ]  Copy matches voice (**aosenuma** lowercase, warm, concise)

### PR snippet (copy/paste)

**UI/UX compliance**

- `design.md` link:
- Figma library + frame (or N/A):
- Tokens only: Yes / No
- ShadCN-first (fork documented): Yes / No
- States: Loading / Empty / Error / Success
- Accessibility checks: Yes / No
- Exceptions file (if any):

---

## New project / new frame checklist (Apr 14 baseline)

**Canonical location (this page).** Use this before marking a **new Figma file or frame** as dev-ready. **5 · Governance & shipping** links here only—do not fork the list into a second copy.

- [ ]  **Semantic color variables only** on production frames (`primary`, `deep`, `background`, `destructive`, … — aligned to `globals.css` / Figma semantic collections).
- [ ]  **Named text and spacing styles** (no orphan font sizes; **8pt** layout rhythm with **4pt** micro spacing inside components).
- [ ]  **Hover, focus-visible, disabled** (and **pressed** / **loading** / **selected** where the pattern applies) designed or explicitly documented — see the **Authoritative button state matrix** and controls sections in [4 · Components & patterns](4%20%C2%B7%20Components%20&%20patterns%203454544eeb4281479040ce5bd99406c7.md).
- [ ]  **Touch targets ≥ 44×44px** for every interactive control (extend invisible hit slop when the visible control is smaller).
- [ ]  **Canonical library + frame links** on the ticket or PR (or **N/A** with reason logged in `docs/design-exceptions.md`).
- [ ]  **Density context** labeled on the frame (**Default** / **Marketing** / **Admin**) — see **Density & product context** in [4 · Components & patterns](4%20%C2%B7%20Components%20&%20patterns%203454544eeb4281479040ce5bd99406c7.md).
- [ ]  **Figma integration hygiene** — if components show **“fix now”** or won’t open, run the triage in [5 · Governance & shipping](../Process%20&%20Governance/5%20%C2%B7%20Governance%20&%20shipping%203454544eeb4281808c68e067d0b6a0f7.md) → *Figma integration (workflow)* before treating it as a UX bug.