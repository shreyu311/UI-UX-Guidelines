# UI/UX guidelines

## aosenuma UI/UX guidelines

This page is the **canonical entry** for product UI: **color, typography, layout, components, states, accessibility, and in-product language**. Engineering pins the same rules in **`design.md`** (`docs/design.md` or repo root). Approved deviations live in **`docs/design-exceptions.md`**.

### What this standard covers

- **Comprehensive UI coverage:** rules apply to **every shipped UI primitive** (actions, forms, selection, navigation, feedback, data display, overlays, layout). Missing guidance is **missing spec**, not optional taste—see the **UI element inventory** in [1 · Scope & principles](Standards/1%20%C2%B7%20Scope%20&%20principles%203454544eeb42810c89b3d3e4ef563c43.md) and the authoritative specs in [4 · Components & patterns](Standards/4%20%C2%B7%20Components%20&%20patterns%203454544eeb4281479040ce5bd99406c7.md).
- **Visual documentation for color:** recurring patterns ship with **Figma frames or PNGs on real components** (hero/gradient, chrome, cards on background, primary vs secondary CTAs, accent discipline). Example slots + checklist: **Brand, layout & tokens** and **Style Card**; **new frame** hygiene: [1 · Scope & principles](Standards/1%20%C2%B7%20Scope%20&%20principles%203454544eeb42810c89b3d3e4ef563c43.md) → *New project / new frame checklist (Apr 14 baseline)*.
- **Gradients:** only the **approved primary gradient** (**135deg**, **#164F5B → #208692**), token-backed—no decorative one-offs unless logged as an exception.

### Visual swatches (hub — link out)

The hub stays text-first; **Figma / PNG proof** for palette application lives in [2 · Brand, layout & tokens](Standards/2%20%C2%B7%20Brand,%20layout%20&%20tokens%203454544eeb4281ce92bbf7eb90df3835.md) (*Visual swatches* + *Embedded gallery*) and [3 · Style Card for UI/UX](Standards/3%20%C2%B7%20Style%20Card%20for%20UI%20UX%203454544eeb428013a31df04ad5caa2e2.md) (*Embedded pattern gallery*).

<aside>
🖼️

**Apr 14 bar:** reviewers should open **embedded Figma** (or dated PNGs) for hero gradient, chrome, cards, CTAs, accent discipline, and semantic states — not generated placeholder tiles.

</aside>

- **Full brand palette at a glance:**

| Swatch name | Hex | Usage |
| --- | --- | --- |
| Teal 700 (Primary hover) | **#164F5B** | Gradient start, hover fill for primary buttons |
| Teal 500 (Primary default) | **#208692** | Gradient end, default CTA fill, links |
| Sage wash | **#E5EADF** | Hover wash for outlined/ghost buttons, subtle surface |
| Destructive default | **#DC2626** | Destructive button fill, error icon color |
| Destructive hover | **#B91C1C** | Destructive button hover |
| Disabled fill | **#D1D5DB** | Disabled button background |
| Disabled text | **#9CA3AF** | Disabled button/ghost text |
| Success green | **#16A34A** | Success states, confirmations |
| Warning amber | **#F59E0B** | Warning states, missing info |

### Semantic color (non-negotiable)

| Role | Token family | Hex | Use for | Never use for |
| --- | --- | --- | --- | --- |
| **Primary / Teal** | `primary` | **#208692** (default) · **#164F5B** (hover/dark) | CTAs, links, focus rings, active states | Errors, failure states |
| **Success / Green** | `success` | **#16A34A** (base) · **#DCFCE7** (bg) | Confirmation, completed states, success toasts | Warning or error messaging |
| **Warning / Amber** | `warning` | **#F59E0B** (base) · **#FEF3C7** (bg) | Non-blocking risk, missing required info before submit | Substitute for red / blocking errors |
| **Destructive / Red** | `destructive` | **#DC2626** (base) · **#B91C1C** (hover) · **#FEE2E2** (bg) | Blocking errors, validation failures, irreversible danger, critical alerts | Marketing emphasis, success, routine info |
| **Neutral / Gray** | `muted` | **#6B7280** (text) · **#D1D5DB** (border) · **#F3F4F6** (bg) | Disabled states, secondary text, borders, backgrounds | Active interactive elements |
| **Info / Calm** | `info` | **#3B82F6** (base) · **#EFF6FF** (bg) | Informational banners, tooltips, non-urgent notices | Errors or warnings |
- Full psychology, edge cases, and Figma proof expectations: **Brand, layout & tokens** → *Semantic palette*.

### UI element map (hub view)

The **master inventory** lives in **Scope & principles**. Use this compact map for navigation.

| Category | Where to read |
| --- | --- |
| Foundations (color, type, grid, radius, shadows) | [2 · Brand, layout & tokens](Standards/2%20%C2%B7%20Brand,%20layout%20&%20tokens%203454544eeb4281ce92bbf7eb90df3835.md) |
| Components, states, patterns, content, accessibility | [4 · Components & patterns](Standards/4%20%C2%B7%20Components%20&%20patterns%203454544eeb4281479040ce5bd99406c7.md) |
| Style card / poster | [3 · Style Card for UI/UX](Standards/3%20%C2%B7%20Style%20Card%20for%20UI%20UX%203454544eeb428013a31df04ad5caa2e2.md) |
| Governance, shipping checklist, exceptions | [5 · Governance & shipping](Process%20&%20Governance/5%20%C2%B7%20Governance%20&%20shipping%203454544eeb4281808c68e067d0b6a0f7.md) |

### Buttons at a glance

Full matrix (hover, pressed, focus, disabled, loading, selected) and spacing: [4 · Components & patterns](Standards/4%20%C2%B7%20Components%20&%20patterns%203454544eeb4281479040ce5bd99406c7.md) → *Authoritative button state matrix*. **Heights** 48 / 40 / 32 · **large CTA padding** **32px** horizontal per side (workshop demos sometimes cite **30px** — **snap to 32px** on the **8pt** grid unless a **logged exception**) · **touch target** ≥ 44×44px.

| Reference label | ShadCN variant | Default | Hover (fill) | Disabled (summary) |
| --- | --- | --- | --- | --- |
| Contained | primary | **#208692** on white label | **#164F5B** | **#D1D5DB** / **#9CA3AF** |
| Outlined | secondary | muted border, deep text | wash **#E5EADF** | muted border + **#9CA3AF** text |
| Text | ghost | transparent, deep text | wash **#E5EADF** | **#9CA3AF** text |
| Destructive | destructive | **#DC2626** | **#B91C1C** | muted neutrals |

### Principles

- **Tokens first:** ShadCN + Tailwind CSS variables — no orphan hex on shipped UI.
- **Components first:** ShadCN primitives and documented variants; fork only with a written exception.
- **States required:** loading, empty, error, and success on meaningful **surfaces**; **controls** also define interaction states (see Components).
- **Accessible by default:** keyboard paths, visible focus, meaningful contrast, respectful motion.
- **Figma matches code:** semantic variables and component names mirror `globals.css` and the implementation library.
- **Aosenuma-branded by default:** anything produced from this hub — prototypes from **Claude Design / Claude Code, Figma, Stitch**, plus **PPTs, templates, decks, and exported prototypes** — ships with **Aosenuma branding applied by default** (logo, brand palette, gradient, typography) on **every page, slide, frame, or template variant**. Unbranded output is treated as a defect, not a draft.

### Aosenuma branding rule (binding)

<aside>
🦆

**Scope:** every artifact created using this UI/UX guidelines page — including AI-generated prototypes (**Claude Design, Claude Code, Figma, Stitch**), **PowerPoint / Keynote decks, templates, design files, and exported prototypes** — must carry **Aosenuma branding by default**.

</aside>

**Required on every page / slide / frame / template:**

- [ ]  **Aosenuma logo** placed per the brand assets page (see [7 · Brand assets (logo & brandbook)](Standards/7%20%C2%B7%20Brand%20assets%20(logo%20&%20brandbook)%203484544eeb4281bcbe84ef71abb8c1ff.md)) — title slide / cover frame, and a smaller mark on subsequent pages.
- [ ]  **Brand palette** — semantic teal **#208692** for primary, hover **#164F5B**, approved gradient **135deg #164F5B → #208692**, plus the full semantic table above. No off-brand accents.
- [ ]  **Typography** — Inter (sans) and the documented type scale; mono only where specified.
- [ ]  **Surface treatment** — backgrounds, cards, and chrome match the **Style Card** proof in [3 · Style Card for UI/UX](Standards/3%20%C2%B7%20Style%20Card%20for%20UI%20UX%203454544eeb428013a31df04ad5caa2e2.md).
- [ ]  **Footer / metadata** — workspace label "[aosenuma.AI](http://aosenuma.AI)" and document owner where the artifact format supports it (decks, templates, exported PDFs).

**Where it applies:**

| Artifact type | Where branding must appear | Source of truth |
| --- | --- | --- |
| **Claude Design / Claude Code prototypes** | Every frame and exported screen — logo in app chrome or cover, tokens from `globals.css` | Ch. 2 + 4, this hub |
| **Figma files & libraries** | Cover page, every frame title block, component thumbnails | Canonical Figma library |
| **Stitch prototypes** | App shell + first/last screen of every flow | This hub + brand assets |
| **PPT / Keynote decks** | Title slide, every content slide footer, closing slide | Aosenuma deck template |
| **Templates (Notion, doc, deck, repo scaffolds)** | Header / cover, plus any repeating page or section header | Brand assets + this hub |
| **Exported prototypes / PDFs** | Cover, page header or footer on every page | Brand assets |

**Exceptions:** any unbranded artifact must be logged in **`docs/design-exceptions.md`** with reason, screenshot, and reviewer — same process as token / component exceptions in [5 · Governance & shipping](Process%20&%20Governance/5%20%C2%B7%20Governance%20&%20shipping%203454544eeb4281808c68e067d0b6a0f7.md).

### Workflow — Claude Design → Claude Code (operating loop)

<aside>
⚙️

The full **operating loop** for the system has its own chapter: [6 · Workflow — Claude Design → Claude Code](Workflow%20&%20Tooling/6%20%C2%B7%20Workflow%20%E2%80%94%20Claude%20Design%20%E2%86%92%20Claude%20Code%203474544eeb4281568702e4dd71f825a6.md). It is **bound** by chapters 1 → 5 and does **not** replace this hub or the Figma library.

</aside>

#### Inputs (single source of truth)

- **Spec:** this hub + chapters **1 · Scope** (UI element inventory), **2 · Brand, layout & tokens** (semantic palette, gradient, type, grid, radius, shadows), **3 · Style Card** (visual proof), **4 · Components & patterns** (state matrices, accessibility), **5 · Governance** (shipping checklist, exceptions).
- **Code:** the repo `globals.css` + ShadCN/Tailwind primitives — **token names** in design must match.
- **Figma library:** canonical mirror of tokens + components (kept in sync with code).

#### Loop (summary — see ch. 6 for detail)

| Step | What happens | Bound by |
| --- | --- | --- |
| **0 · Onboard** | One-time per project: point Claude Design at the **repo**  • this hub (chapters 2 + 4) so it learns the **aosenuma design system** (semantic teal `#208692`, destructive `#DC2626`, gradient 135° **#164F5B → #208692**, 8pt grid, ShadCN component variants). Confirm inferred system matches the **Semantic color** table. | Ch. 2 + 4 |
| **1 · Brief** | Capture intent in plain language **or** import (PRD doc, Notion page, web capture). Use **named elements** from the **UI element inventory** (ch. 1) — e.g. *“KPI card”*, *“directory grid card”*, *“slide-over panel”*. | Ch. 1 |
| **2 · Generate** | Claude Design returns initial frames using the onboarded system. Reject any output that uses **raw hex**, off-token spacing, or non-ShadCN variants — re-prompt with the token name. | Ch. 2 |
| **3 · Refine** | Use inline comments + AI sliders to adjust **layout / color / spacing**. Snap spacing to **4 / 8 / 16 / 24 / 32 / 48 / 64**. Require all interactive states from the **button state matrix** (default, hover, pressed, focus, disabled, loading, selected where relevant). Verify **focus ring** is visible and **hit area ≥ 44×44px**. | Ch. 4 |
| **4 · Visual cross-check** | Compare frames against **Style Card** PNGs / **Visual swatches** in chapters 2 and 3 (hero gradient, chrome, cards on background, primary vs. secondary CTAs, accent discipline, semantic states). Reviewers must open the **embedded Figma / dated PNG**, not generated tiles (Apr 14 bar). | Ch. 2 + 3 |
| **5 · Handoff to Claude Code** | One-command bundle from Claude Design → **Claude Code**, which writes **ShadCN-first** code into the repo. PR uses the standard checklist: tokens (no orphan hex), ShadCN variants (or logged exception), states present, a11y verified, **Figma frame** linked. | Ch. 5 |
| **6 · Mirror back** | Export final frames into the **canonical Figma library** so Dev Mode stays aligned with code. Update the project’s **UI/UX Compliance** page with the new frames and the spec sections they satisfy. | Library + per-project compliance |

#### Mapping to the phased rollout (A–E)

| Phase | Where it lands in the loop |
| --- | --- |
| **A — Inventory & categories** | Step **1 · Brief** — element names feed the prompts; missing items go back to ch. 1. |
| **B — Visual color & gradients** | Steps **0 · Onboard**  • **4 · Visual cross-check** — palette and gradient validated against Style Card. |
| **C — Buttons → other components** | Step **3 · Refine** — every variant must show the full state matrix from ch. 4. |
| **D — Written rules tied to visuals** | Steps **3 + 4** — each frame links back to the rule it satisfies (do/don’t in ch. 4). |
| **E — Stakeholder closure** | Step **4** — live Claude Design sessions replace some review meetings; stakeholders react in-context. |

#### Guardrails (do not bypass)

- **Semantic color** is the law: red **only** for destructive/blocking errors; teal `#208692` for CTA/links/focus; warning amber, success green, info calm-blue per the **Semantic color** table. Any divergence = exception.
- **Tokens, not hex:** Claude Design output must reference token names. If a generated frame ships raw hex, fix in chat (“use `primary` and `border` tokens”) before handoff.
- **States required:** loading / empty / error / success on surfaces; full interaction matrix on controls.
- **Accessibility:** keyboard path, visible focus, contrast, motion respect — verified before step 5.
- **Spacing & radius:** 8pt grid; default radius **12px** (`--radius` 0.75rem) unless excepted.
- **Aosenuma branding by default:** anything generated from this hub — Claude Design / Claude Code prototypes, Figma frames, Stitch flows, PPT/Keynote decks, templates, exported prototypes — must include the **Aosenuma logo, brand palette, gradient, and typography** on **every page, slide, frame, or template variant**. Unbranded output = defect; log under exceptions if intentional.

#### Governance & privacy

- **Owner:** Shreyas Shirke (UI/UX Standards Owner). Pilots: one project per chapter (suggested: Executive Dashboard for ch. 4 components; Woodside for ch. 2 tokens).
- **Privacy posture:** Claude Design stores **design-system representations** (not raw source files); when linked to a codebase, repo data stays local and is not used for training. Enterprise admins can keep the tool disabled by default.
- **Exceptions:** any Claude Design output that breaks tokens, states, or semantic color is logged in **`docs/design-exceptions.md`** with screenshot + reason, per chapter **5 · Governance**.
- **Status:** Claude Design is in **research preview** (Apr 2026) — treat it as **assistive**; this hub + Figma library remain the **binding** sources.

#### One-paragraph summary

Briefs (ch. 1) → Claude Design generates against the onboarded **aosenuma** system (ch. 2) → reviewers refine against state matrices (ch. 4) and visual proof (ch. 3) → one-command handoff to **Claude Code** for ShadCN-first implementation (ch. 5) → frames mirrored back into the **Figma library** so design, code, and Notion stay one system. **Full templates, prompts, FAQ, and pilot plan:** [6 · Workflow — Claude Design → Claude Code](Workflow%20&%20Tooling/6%20%C2%B7%20Workflow%20%E2%80%94%20Claude%20Design%20%E2%86%92%20Claude%20Code%203474544eeb4281568702e4dd71f825a6.md).

### Reading order

Read **chapters 1 → 5** in order: **1** scope + inventory, **2** tokens and visual foundations, **3** style card where used, **4** components and patterns, **5** governance and shipping. **Then ch. 6** — [6 · Workflow — Claude Design → Claude Code](Workflow%20&%20Tooling/6%20%C2%B7%20Workflow%20%E2%80%94%20Claude%20Design%20%E2%86%92%20Claude%20Code%203474544eeb4281568702e4dd71f825a6.md) — is the **operating loop** that consumes those five chapters.

## Engineering appendix — [design.md](http://design.md) complete spec (2026-04-22)

*Full checklist from the design-system audit (replaces the earlier short parity block). Basis: Tailwind v4 + ShadCN new-york. A11y floor: WCAG 2.2 AA. TODO: confirm = needs Brand/Design for values not yet in globals.css.*

### [design.md](http://design.md) fragments — Notion UI/UX gaps (paste into Notion or repo)

**Basis:** Tailwind v4 + ShadCN new-york. **A11y:** WCAG 2.2 AA. `TODO: confirm` = needs Brand/Figma.

---

## Index

**Critical (v1):** [tokens](#tokens-map) | [typography](#typography) | [spacing](#spacing) | [radius](#radius) | [shadow](#shadow) | [breakpoints](#breakpoints) | [dark mode](#dark-mode) | [flat links](#links-flat)

**Important (v1.1):** [focus](#focus-ring) | [motion](#motion) | [z-index](#z-index) | [a11y](#a11y-target) | [forms](#forms) | [loading](#loading-skeleton) | [icons](#iconography) | [microcopy](#microcopy) | [exceptions](#exceptions-template) | [versioning](#versioning)

**Nice (v1.2 stubs):** [code examples](#code-examples) | [browsers](#browser-matrix) | [i18n/RTL](#i18n-rtl) | [assets](#assets) | [visual regression](#visual-regression) | [contribution](#contribution) | [Figma URLs](#figma-urls)

---

# Critical (v1)

## Token to code mapping

Semantic role → **CSS var** in `globals.css` → **Tailwind** → **light/dark (HSL)**. Do not use raw hex in components.

| Role | CSS variable | Tailwind | Light | Dark | Use |
| --- | --- | --- | --- | --- | --- |
| Background | `--background` | `bg-background` | `0 0% 100%` | `240 10% 3.9%` | Canvas |
| Foreground | `--foreground` | `text-foreground` | `240 10% 3.9%` | `0 0% 98%` | Body text |
| Card | `--card` | `bg-card` / `text-card-foreground` | (see ShadCN) | (see ShadCN) | Surfaces |
| Popover | `--popover` | `bg-popover` | … | … | Menus, tooltips |
| Primary | `--primary` | `bg-primary` `text-primary-foreground` | `240 5.9% 10%` | `0 0% 98%` / inv. | CTA, emphasis |
| Secondary | `--secondary` | `bg-secondary` | … | … | Secondary actions |
| Muted | `--muted` | `bg-muted` `text-muted-foreground` | … | … | Subdued, skeleton |
| Accent | `--accent` | `bg-accent` | … | … | Row hover, selection |
| Destructive | `--destructive` | `bg-destructive` `text-destructive-foreground` | `0 84.2% 60.2%` | `0 62.8% 30.6%` | Danger |
| Border | `--border` | `border-border` | … | … | Dividers |
| Input | `--input` | `border-input` | … | … | Field border |
| Ring | `--ring` | `ring-ring` (focus) | … | … | Focus ring color |
| Radius | `--radius` | `rounded-lg` base | `0.75rem` | `0.75rem` | See [Radius](#radius) |

### globals.css (ShadCN new-york)

```css
@layer base {
  :root {
    --background: 0 0% 100%;
    --foreground: 240 10% 3.9%;
    --card: 0 0% 100%;
    --card-foreground: 240 10% 3.9%;
    --popover: 0 0% 100%;
    --popover-foreground: 240 10% 3.9%;
    --primary: 240 5.9% 10%;
    --primary-foreground: 0 0% 98%;
    --secondary: 240 4.8% 95.9%;
    --secondary-foreground: 240 5.9% 10%;
    --muted: 240 4.8% 95.9%;
    --muted-foreground: 240 3.8% 46.1%;
    --accent: 240 4.8% 95.9%;
    --accent-foreground: 240 5.9% 10%;
    --destructive: 0 84.2% 60.2%;
    --destructive-foreground: 0 0% 98%;
    --border: 240 5.9% 90%;
    --input: 240 5.9% 90%;
    --ring: 240 5.9% 10%;
    --radius: 0.75rem;
  }
  .dark {
    --background: 240 10% 3.9%;
    --foreground: 0 0% 98%;
    --card: 240 10% 3.9%;
    --card-foreground: 0 0% 98%;
    --popover: 240 10% 3.9%;
    --popover-foreground: 0 0% 98%;
    --primary: 0 0% 98%;
    --primary-foreground: 240 5.9% 10%;
    --secondary: 240 3.7% 15.9%;
    --secondary-foreground: 0 0% 98%;
    --muted: 240 3.7% 15.9%;
    --muted-foreground: 240 5% 64.9%;
    --accent: 240 3.7% 15.9%;
    --accent-foreground: 0 0% 98%;
    --destructive: 0 62.8% 30.6%;
    --destructive-foreground: 0 0% 98%;
    --border: 240 3.7% 15.9%;
    --input: 240 3.7% 15.9%;
    --ring: 240 4.9% 83.9%;
  }
}
```

> `TODO: confirm` brand `--primary` (replace neutral ShadCN default with brand HSL).
> 

---

## Typography

**Sans:** `Inter`, system-ui, sans-serif. **Mono:** `ui-monospace`, `Menlo`, `Consolas`, monospace.  

`TODO: confirm` if brand font replaces Inter for display.

| Token | Size | Rem | Line height | Class |
| --- | --- | --- | --- | --- |
| xs | 12px | 0.75 | 1rem | `text-xs` `leading-4` |
| sm | 14px | 0.875 | 1.25rem | `text-sm` `leading-5` |
| base | 16px | 1 | 1.5rem | `text-base` `leading-6` |
| lg | 18px | 1.125 | 1.75rem | `text-lg` `leading-7` |
| xl | 20px | 1.25 | 1.75rem | `text-xl` `leading-7` |
| 2xl | 24px | 1.5 | 2rem | `text-2xl` `leading-8` |
| 3xl | 30px | 1.875 | 2.25rem | `text-3xl` `leading-9` |
| 4xl | 36px | 2.25 | 2.5rem | `text-4xl` `leading-10` |

**Weights:** `font-normal` 400, `font-medium` 500, `font-semibold` 600 (headings, buttons), `font-bold` 700 sparingly.

**Rule:** default body = `text-base text-foreground`; headings = `font-semibold tracking-tight` where applicable.

## Spacing (Tailwind scale)

8px grid: prefer `2,4,6,8` steps. `space-*` = `n * 0.25rem`.

| Token | px | rem | Example |
| --- | --- | --- | --- |
| 1 | 4 | 0.25 | `p-1` `gap-1` |
| 2 | 8 | 0.5 | `p-2` |
| 3 | 12 | 0.75 | `p-3` |
| 4 | 16 | 1 | `p-4` (default gap) |
| 6 | 24 | 1.5 | `p-6` (cards) |
| 8 | 32 | 2 | `p-8` (CTA padding) |
| 12 | 48 | 3 | section gutters |
| 16 | 64 | 4 | section breaks |

**Layout:** `px-4 md:px-6 lg:px-8` for page gutters. **Touch:** min 44×44px target (overrides tight spacing) — see [A11y](#a11y-target).

## Radius

Base `--radius: 0.75rem` (12px). ShadCN pattern:

| Name | calc | Class | Use |
| --- | --- | --- | --- |
| sm | `var(--radius) - 4px` | `rounded-sm` | chips |
| md | `var(--radius) - 2px` | `rounded-md` | input, button |
| lg | `var(--radius)` | `rounded-lg` | card, modal |
| xl | `var(--radius) + 4px` | `rounded-xl` | large panels |
| 2xl | `var(--radius) + 8px` | `rounded-2xl` | hero (marketing) |

| full | `9999px` | `rounded-full` | avatars, pills |
| --- | --- | --- | --- |

Buttons + inputs: same class (`md`) so they align. No `rounded-none` in product without an exception.

## Shadow / elevation (Tailwind defaults)

| Class | Use |
| --- | --- |
| `shadow-xs` | hairline depth |
| `shadow-sm` | **elevation-card** — cards, rows |
| `shadow-md` | **elevation-popover** — menus, popovers |
| `shadow-lg` | **elevation-modal** — dialog, sheet, toast |
| `shadow-xl` / `2xl` | marketing / rare hero only |

**Dark mode:** add `border border-border` on elevated surfaces; shadow alone is often too weak.

## Breakpoints

| Name | min | Prefix |
| --- | --- | --- |
| sm | 640px | `sm:` |
| md | 768px | `md:` |
| lg | 1024px | `lg:` |
| xl | 1280px | `xl:` |
| 2xl | 1536px | `2xl:` |

Test at **375, 768, 1024, 1440**. App max width often `max-w-screen-xl`.

## Dark mode

**Supported:** `class="dark"` on `<html>`, tokens under `.dark { }` in `globals.css`. Respect `prefers-color-scheme` for default; persist user choice in `localStorage` where applicable. Avoid flash: inline script in `<head>` before paint.

**Rule:** any UI change in a PR: screenshot light + dark.

## Flat links (repo paths for exported Markdown)

Replace Notion-only mentions with repo links:

| Topic | Path |
| --- | --- |
| Scope | `docs/design/1-scope.md` |
| Principles | `docs/design/2-principles.md` |
| Tokens | `docs/design/3-tokens.md` |
| Typography | `docs/design/4-typography.md` |
| Spacing | `docs/design/5-spacing.md` |
| Components | `docs/design/6-components.md` |
| Patterns | `docs/design/7-patterns.md` |
| A11y | `docs/design/8-accessibility.md` |
| Motion | `docs/design/9-motion.md` |
| Exceptions | `docs/design/design-exceptions.md` |
| Changelog | `docs/design/CHANGELOG.md` |

Example: `[Tokens](docs/design/3-tokens.md)`.

---

# Important (v1.1)

## Focus ring

- **Color:** `ring-ring` / `--ring`
- **Width:** 2px  |  **Offset:** 2px  |  **Only** `:focus-visible`

```tsx
className="outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 focus-visible:ring-offset-background"
```

## Motion

| Token | Duration | Use |
| --- | --- | --- |
| fast | 120ms | hover, micro |
| base | 200ms | default transitions |
| slow | 320ms | modal, sheet |

**Reduced motion:** wrap aggressive animation; honor `prefers-reduced-motion: reduce` (shorten or disable motion).

## Z-index scale

| Layer | z-index |
| --- | --- |
| base | 0 |
| dropdown | 1000 |
| sticky | 1100 |
| overlay | 1200 |
| modal | 1300 |
| popover | 1400 |
| toast | 1500 |
| tooltip | 1600 |

Deviations need an [exception](#exceptions-template).

## Accessibility target

**WCAG 2.2 AA:** body text **4.5:1**, large text / UI graphics **3:1** where applicable. **Keyboard:** full operation, focus order, trap in modals, `Esc` to dismiss. **Touch:** **44×44px** minimum targets.

**SR:** labels not placeholder-only; `aria-live` for async errors; icon buttons `aria-label`.

## Form patterns

**Stack:** Label (required `*` + `aria-required`) → control → helper **or** error (not both as primary message).

**Error:** below field, `text-destructive`, `id` linked via `aria-describedby`. Copy: what happened + how to fix.

**Timing:** validate on **blur** (format); debounce **500ms** on type for async checks; full validate on submit. Do not error on first focus.

## Loading & skeleton

- **< 200ms:** no spinner
- **200ms–1s:** inline spinner on action
- **> 1s:** skeleton matching final layout
- **Skeleton:** `animate-pulse` + `bg-muted`, min show **~400ms** to avoid flash
- **Shimmer** only if product explicitly standardizes (default = pulse)

## Iconography

**Default:** Lucide + `lucide-react`. Sizes: 16 / 20 / 24 (`size-4` / `5` / `6`). **Stroke:** 1.5 (default). Inherit `currentColor`. Decorative: `aria-hidden`. Meaningful alone: parent gets `aria-label`.

## Content / microcopy

**Buttons:** Save / Cancel / Continue / Delete (destructive) vs Remove (reversible) / **Create X** vs **Add X**.

**Empty state:** one line what/why empty + one primary CTA.  

**Error:** what + (optional) why + what to do next. Avoid cutesy “Oops!”, vague “Something went wrong” without retry path.

## Design exceptions (entry format)

File: `docs/design/exceptions/<id>.md`

```yaml
---
id: EXC-2026-001
component: path/Component
owner: "@github"
reviewer: "@github"
created: 2026-04-22
expires: 2026-10-22
status: active
rationale: One line why this deviation is allowed.
screenshot: ./assets/exc-2026-001.png
---
## Context
## Deviation
## Mitigation
## Review
```

## Versioning

Header on canonical doc:

```yaml
version: 1.0.0
last-updated: 2026-04-22
owners: ["@team"]
status: draft | adopted
```

**Changelog:** append-only table (date, version, change, author). Any doc change in a PR adds a row.

---

# Nice-to-have (v1.2 — stubs)

## Code examples (TSX)

TODO: one snippet per ShadCN component (variant + tokens). Self-verifying copy-paste.

## Browser / device matrix

TODO: last 2 Chrome, Edge, Firefox, Safari; iOS Safari 16+; Android Chrome recent. No IE.

## Internationalization & RTL

TODO: locales, logical properties (`ps-` `pe-` `start` `end`), date/number formatting.

## Image & asset standards

TODO: logo clear space, ratios, OG 1200×630, favicons.

## Visual regression testing

TODO: Chromatic / Percy / Playwright — what is snapshotted, viewports, review process.

## Contribution process

TODO: PR template for token/component changes, reviewers, SLA, checklist (a11y, L+D screenshots, changelog).

## Figma source of truth

TODO: design file URL, library URL, prototype — for engineers who skip Notion.

<aside>
📌

**Source on disk (UTF-8):** `Desktop/Design/design-md-fragments.md` — same material as this appendix for repo export (extended ShadCN blocks, exceptions YAML, versioning).

</aside>

---

## Reference documents (read in sequence)

Authoritative chapters this hub binds. Read **1 → 9** in order; chapters 1–5 are the standards, chapter 6 is the operating loop, chapter 7 is brand assets (source for the Aosenuma branding rule), chapter 8 is engineering workflows, and chapter 9 is the consolidation map across Notion / Repo / Stitch / Figma.

### Standards (chapters 1–5)

| # | Chapter | What it covers |
| --- | --- | --- |
| **1** | [1 · Scope & principles](Standards/1%20%C2%B7%20Scope%20&%20principles%203454544eeb42810c89b3d3e4ef563c43.md) | UI element inventory, scope, new-frame checklist |
| **2** | [2 · Brand, layout & tokens](Standards/2%20%C2%B7%20Brand,%20layout%20&%20tokens%203454544eeb4281ce92bbf7eb90df3835.md) | Semantic palette, gradient, typography, grid, radius, shadows |
| **3** | [3 · Style Card for UI/UX](Standards/3%20%C2%B7%20Style%20Card%20for%20UI%20UX%203454544eeb428013a31df04ad5caa2e2.md) | Visual proof — embedded Figma / dated PNG gallery |
| **4** | [4 · Components & patterns](Standards/4%20%C2%B7%20Components%20&%20patterns%203454544eeb4281479040ce5bd99406c7.md) | Authoritative component specs, state matrices, accessibility |
| **5** | [5 · Governance & shipping](Process%20&%20Governance/5%20%C2%B7%20Governance%20&%20shipping%203454544eeb4281808c68e067d0b6a0f7.md) | Shipping checklist, exceptions process, ownership |

### Workflow & tooling (chapters 6–9)

| # | Chapter | What it covers |
| --- | --- | --- |
| **6** | [6 · Workflow — Claude Design → Claude Code](Workflow%20&%20Tooling/6%20%C2%B7%20Workflow%20%E2%80%94%20Claude%20Design%20%E2%86%92%20Claude%20Code%203474544eeb4281568702e4dd71f825a6.md) | Operating loop: brief → generate → refine → handoff → mirror |
| **7** | [7 · Brand assets (logo & brandbook)](Standards/7%20%C2%B7%20Brand%20assets%20(logo%20&%20brandbook)%203484544eeb4281bcbe84ef71abb8c1ff.md) | Logo files, clear space, brandbook — source for the Aosenuma branding rule |
| **8** | [8 · Github Workflows Code](Workflow%20&%20Tooling/8%20%C2%B7%20Github%20Workflows%20Code%2034a4544eeb4280e19b6cd7a29d505a51.md) | CI/CD checks, PR automation, design-system gates in GitHub Actions |
| **9** | [9 · Consolidation map — Notion · Repo · Stitch · Figma](Workflow%20&%20Tooling/9%20%C2%B7%20Consolidation%20map%20%E2%80%94%20Notion%20%C2%B7%20Repo%20%C2%B7%20Stitch%20%C2%B7%20F%2034a4544eeb4281b5a45bd1d1321b52bf.md) | Crosswalk of where each artifact lives and which is canonical |

### Section hubs (parents of the chapters above)

| Hub | Contains |
| --- | --- |
| [UI/UX Guidelines](../UI%20UX%20Guidelines%2034b4544eeb4280b380c1c4b7e5addcfa.md) | This hub — single source of truth landing page |
| [Standards](Standards%20324f2b3f65974047be3f428f74728975.md) | Parent of chapters 1–4 + 7 |
| [Process & Governance](Process%20&%20Governance%2082a235b3f3ae44e184dac8cad68e797c.md) | Parent of chapter 5 + governance playbooks |
| [Workflow & Tooling](Workflow%20&%20Tooling%205ec6517d3604407fb22045305046ba1c.md) | Parent of chapters 6, 8, 9 + design catalog |
| [Planning & Meetings](Planning%20&%20Meetings%20600f402b0ea7461b9ec77523708de715.md) | Working plans, meeting notes, system-plan SSOT |
| [Projects](Projects%20806da2d7b16e4d29bca33f66a6e194ae.md) | Per-project UI/UX compliance trackers (Executive Dashboard, Woodside, RapdAI, StakeAI, etc.) |

### Companion references (CSV-ready + onboarding + history)

| Reference | Use |
| --- | --- |
| [7 · Design catalog — reference index (CSV import)](Workflow%20&%20Tooling/7%20%C2%B7%20Design%20catalog%20%E2%80%94%20reference%20index%20(CSV%20import)%203374544eeb4281839c3fd35dde864187.md) | **Pre-structured for CSV import** — use this for spreadsheet/CSV exports of the design system index |
| [Claude Design Using - UI/UX Guidelines ](Claude%20Design%20Using%20-%20UI%20UX%20Guidelines%203484544eeb4280188264d481b68e5759.md) | Practical onboarding + prompts for the Claude Design loop (companion to ch. 6) |
| [Governance & rollout](Process%20&%20Governance/5%20%C2%B7%20Governance%20&%20shipping/Archive%20%E2%80%94%20superseded%2012-way%20split%20(2026-04-17)/Governance%20&%20rollout%203454544eeb4281908299c56566009e0b.md) | Phased program rollout (A → E), historical context for ch. 5 |
| [UI/UX System Proposal Plan](Planning%20&%20Meetings/UI%20UX%20System%20Proposal%20Plan%203374544eeb42816bb76ff44b58bce073.md) | Original system proposal — background context |
| [3 · UI/UX system plan — process & validation (SSOT)](Process%20&%20Governance/3%20%C2%B7%20UI%20UX%20system%20plan%20%E2%80%94%20process%20&%20validation%20(SSOT%203374544eeb42810f9015e8d48d5453af.md) | Process + validation SSOT (executable rules pinned in `design.md`) |
| [5 · UI/UX governance — PM execution playbook](Process%20&%20Governance/5%20%C2%B7%20UI%20UX%20governance%20%E2%80%94%20PM%20execution%20playbook%20e112617dc0d74306a44fe55ac121ef52.md) | PM execution playbook for the UI/UX governance gates |
| [UI/UX Reporting Process & Prototyping Standards — Mandatory Compliance](Process%20&%20Governance/UI%20UX%20Reporting%20Process%20&%20Prototyping%20Standards%20%E2%80%94%20%20e1a5cc1e61df4667b06403c01b3643fc.md) | Mandatory compliance checklist template (duplicate per project) |

<aside>
⚠️

**CSV export caveat:** Notion exports a *page* as **Markdown/HTML**, not CSV. Only **databases** export to CSV. So:
• Exporting **this hub** as Markdown will preserve the tables above as readable Markdown rows — not a true CSV.
• For a real CSV of the design-system index, use **[7 · Design catalog — reference index (CSV import)](Workflow%20&%20Tooling/7%20%C2%B7%20Design%20catalog%20%E2%80%94%20reference%20index%20(CSV%20import)%203374544eeb4281839c3fd35dde864187.md)** — it is already structured for CSV.
• To get all linked chapters in one bundle: **Export → "Markdown & CSV" with "Include subpages" toggled on** from the **[UI/UX Guidelines](../UI%20UX%20Guidelines%2034b4544eeb4280b380c1c4b7e5addcfa.md)** page.

</aside>

<aside>
📚

**Repo mirrors:** the same chapters are pinned in `docs/design/` (`1-scope.md` → `9-motion.md`), with deviations in `docs/design-exceptions.md` and history in `docs/design/CHANGELOG.md`. Keep Notion ↔ repo ↔ Figma library in sync.

</aside>