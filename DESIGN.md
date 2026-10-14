# DESIGN.md: core design and prototyping rules

**Version 1.0.0** · Layer A of the framework · Brand-agnostic

This file is the single source of the core rules. It contains no brand values. Brand-specific decisions (colors, fonts, logo, voice) live in your brand book, `brandbook/brandbook.md`, created from [`brandbook/brandbook.template.md`](brandbook/brandbook.template.md).

---

## 0. How to read this file

**Audience:** designers, engineers, and AI design or coding assistants.

**Rule levels** (capitalized on purpose):

| Level | Meaning | Can a brand book change it? |
| --- | --- | --- |
| **MUST** | Mandatory. Mostly accessibility, usability, and responsive-design baselines. | No. |
| **SHOULD** | The default. Deviate only for a documented reason (in the brand book or the exception log). | Yes, with a documented reason. |
| **MAY** | Optional. | Yes. |

**Rule IDs** such as `CLR-1` are used by the review checklist in [`docs/validation.md`](docs/validation.md), by audits, and in AI self-check reports.

**Token references** are written in dot notation, for example `color.action.primary`. In CSS the same token is the custom property `--color-action-primary`.

---

## 1. How the core rules and the brand book work together

Apply these sources in this order of precedence:

1. **MUST rules in this file**: always apply. Nothing overrides them.
2. **Brand book values** (`brandbook/brandbook.md`): decide colors, typography, logo, shape, density, and voice wherever this file allows a choice.
3. **SHOULD defaults in this file**: apply wherever the brand book is silent.
4. **Neutral fallbacks** ([§3.4](#34-neutral-fallback-values) and [§3.5](#35-fallback-scales)): used when a value is needed but the brand book doesn't provide it.

A brand-book field still containing a square-bracket placeholder such as `[PRIMARY COLOR]` counts as **not provided**.

| ID | Rule |
| --- | --- |
| BRD-1 | MUST read the brand book before producing UI. If no brand book exists, use the neutral fallbacks for everything and say so. |
| BRD-2 | MUST NOT invent brand identity: no made-up brand names, logos, colors, fonts, or voice. Use the fallback and flag the gap. |
| BRD-3 | MUST apply brand values through tokens only. A brand value that would break a MUST rule (for example, a color that fails contrast as text) is not applied in that role; use the compliant alternative described in [`brandbook/README.md`](brandbook/README.md#when-a-brand-value-breaks-a-must-rule) and report it. |
| BRD-4 | SHOULD report which brand-book fields were used and which fell back, in the pull request description or the AI response. |
| BRD-5 | MUST keep brand values out of this file. To change a core rule, follow [`docs/customization.md`](docs/customization.md). |

---

## 2. Principles

1. **Clarity over decoration.** Every element helps someone understand or act.
2. **Consistency over novelty.** Reuse an existing pattern before inventing one.
3. **Accessible by default.** Accessibility is a requirement, not a polish step.
4. **Tokens, not values.** Named tokens carry every visual decision.
5. **Every state is designed.** Not just the happy path.
6. **One source of truth.** Rules live here; brand values live in the brand book; everything else is derived from them.

**When rules or goals conflict**, resolve in this order: accessibility → usability and clarity → consistency → brand expression → visual preference. If a conflict can't be resolved within the rules, log an exception ([`templates/exception-log.md`](templates/exception-log.md)).

---

## 3. Design tokens

### 3.1 Tiers

| Tier | Purpose | Example |
| --- | --- | --- |
| **Primitive** | Raw palette and scales. Not used directly in UI. | `violet.700 = #6D28D9` |
| **Semantic** | Purpose, mapped to a primitive. Used in UI. | `color.action.primary → violet.700` |
| **Component** | Optional, for one component's needs. | `button.primary.background → color.action.primary` |

| ID | Rule |
| --- | --- |
| TOK-1 | MUST style UI with semantic or component tokens. Raw values (hex codes, pixel sizes, durations) appear only where tokens are defined. |
| TOK-2 | MUST NOT create tokens ad hoc inside a screen or component. Add tokens through [`docs/customization.md`](docs/customization.md#adding-a-token). |
| TOK-3 | SHOULD name tokens by purpose, not appearance (`color.status.danger`, not `color.red`). |
| TOK-4 | SHOULD keep token names stable and change values instead; renaming is a breaking change. |

### 3.2 Naming

`{category}.{role}.{variant}.{state}`, omitting parts that don't apply, for example `color.text.muted`, `color.action.primary.hover`, `space.4`, `radius.md`.

CSS mapping: replace dots with hyphens and prefix `--`, so `color.text.muted` → `--color-text-muted`.

### 3.3 Required semantic color tokens

| Token | Used for |
| --- | --- |
| `color.surface.default` | Page and main surface background |
| `color.surface.subtle` | Secondary surfaces: panels, table stripes, wells |
| `color.text.default` | Body text and headings |
| `color.text.muted` | Secondary text: captions, metadata |
| `color.text.disabled` | Text of disabled controls |
| `color.text.on-action` | Text and icons placed on `color.action.primary` |
| `color.border.subtle` | Decorative dividers only (not control boundaries) |
| `color.border.control` | Boundaries of inputs and other controls |
| `color.action.primary` | Primary buttons, links, selected states |
| `color.action.primary.hover` | Hover and pressed state of primary actions |
| `color.focus.ring` | Keyboard focus indicator |
| `color.status.success` | Success messages and icons |
| `color.status.warning` | Warnings and non-blocking risk |
| `color.status.danger` | Errors and destructive actions |
| `color.status.info` | Neutral information |

### 3.4 Neutral fallback values

Used when the brand book doesn't provide a value. They are deliberately plain: grays, with one conventional blue for actions. They are not a brand.

| Token | Light | Dark | Measured contrast (WCAG) |
| --- | --- | --- | --- |
| `color.surface.default` | `#FFFFFF` | `#0A0A0A` | n/a (background) |
| `color.surface.subtle` | `#F5F5F5` | `#171717` | n/a (background) |
| `color.text.default` | `#171717` | `#FAFAFA` | 17.93:1 / 18.97:1 on default surface |
| `color.text.muted` | `#525252` | `#A3A3A3` | 7.81:1 / 7.85:1 on default surface |
| `color.text.disabled` | `#A3A3A3` | `#737373` | exempt for disabled controls (see A11Y notes) |
| `color.text.on-action` | `#FFFFFF` | `#0A0A0A` | 6.70:1 / 7.79:1 on `color.action.primary` |
| `color.border.subtle` | `#E5E5E5` | `#262626` | decorative only |
| `color.border.control` | `#737373` | `#737373` | 4.74:1 / 4.18:1 on default surface |
| `color.action.primary` | `#1D4ED8` | `#60A5FA` | 6.70:1 / 7.79:1 as text on default surface |
| `color.action.primary.hover` | `#1E40AF` | `#93C5FD` | 8.72:1 / 10.98:1 with `color.text.on-action` |
| `color.focus.ring` | `#1D4ED8` | `#60A5FA` | 6.70:1 / 7.79:1 against default surface |
| `color.status.success` | `#15803D` | `#4ADE80` | 5.02:1 / 11.36:1 |
| `color.status.warning` | `#B45309` | `#FBBF24` | 5.02:1 / 11.86:1 |
| `color.status.danger` | `#B91C1C` | `#F87171` | 6.47:1 / 7.16:1 |
| `color.status.info` | `#0369A1` | `#38BDF8` | 5.93:1 / 9.24:1 |

Status colors are measured as text on `color.surface.default`. In light mode, white text on each status color passes too (5.02:1 to 6.47:1), so they also work as filled badges.

### 3.5 Fallback scales

**Typography**

| Token | Fallback |
| --- | --- |
| `font.family.sans` | `system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif` |
| `font.family.heading` | Same as `font.family.sans` |
| `font.family.mono` | `ui-monospace, SFMono-Regular, Menlo, Consolas, monospace` |
| `font.weight.*` | `regular 400`, `medium 500`, `semibold 600`, `bold 700` |

| Token | Size / line height (px) | Typical role |
| --- | --- | --- |
| `font.size.xs` | 12 / 16 | Captions, legal text |
| `font.size.sm` | 14 / 20 | Secondary text, dense tables |
| `font.size.base` | 16 / 24 | Body text |
| `font.size.lg` | 18 / 28 | Lead text, H4 |
| `font.size.xl` | 20 / 28 | H3 |
| `font.size.2xl` | 24 / 32 | H2 |
| `font.size.3xl` | 30 / 36 | H1 |
| `font.size.4xl` | 36 / 40 | Display |

**Spacing** (4 px base): `space.0` 0 · `space.1` 4 · `space.2` 8 · `space.3` 12 · `space.4` 16 · `space.6` 24 · `space.8` 32 · `space.12` 48 · `space.16` 64 · `space.24` 96 (px).

**Shape and depth**

| Token | Fallback |
| --- | --- |
| `radius.none` / `radius.sm` / `radius.md` / `radius.lg` / `radius.full` | 0 / 4 / 8 / 12 / 9999 px (controls default to `radius.md`, cards and dialogs to `radius.lg`) |
| `border.width.default` | 1 px |
| `shadow.sm` | `0 1px 2px rgba(0, 0, 0, 0.06)`: cards, raised rows |
| `shadow.md` | `0 4px 8px rgba(0, 0, 0, 0.08)`: menus, popovers |
| `shadow.lg` | `0 12px 28px rgba(0, 0, 0, 0.14)`: dialogs, drawers |

**Motion, layout, layering**

| Token | Fallback |
| --- | --- |
| `duration.fast` / `duration.base` / `duration.slow` | 100 / 200 / 300 ms |
| `easing.standard` / `easing.exit` | `cubic-bezier(0.2, 0, 0, 1)` / `cubic-bezier(0.4, 0, 1, 1)` |
| `breakpoint.sm` / `.md` / `.lg` / `.xl` | 640 / 768 / 1024 / 1280 px (min-width) |
| `z.base` / `z.dropdown` / `z.sticky` / `z.overlay` / `z.modal` / `z.toast` / `z.tooltip` | 0 / 10 / 20 / 30 / 40 / 50 / 60 |

### 3.6 Example: tokens as CSS custom properties

```css
:root {
  --color-surface-default: #ffffff;
  --color-text-default: #171717;
  --color-action-primary: #1d4ed8;
  --color-text-on-action: #ffffff;
  --space-4: 16px;
  --radius-md: 8px;
}

@media (prefers-color-scheme: dark) {
  :root {
    --color-surface-default: #0a0a0a;
    --color-text-default: #fafafa;
    --color-action-primary: #60a5fa;
    --color-text-on-action: #0a0a0a;
  }
}

.button-primary {
  background: var(--color-action-primary);
  color: var(--color-text-on-action);
  padding: 0 var(--space-4);
  border-radius: var(--radius-md);
}
```

---

## 4. Color

| ID | Rule |
| --- | --- |
| CLR-1 | MUST meet contrast minimums: 4.5:1 for text; 3:1 for large text (at least 24 px, or 18.66 px bold); 3:1 for control boundaries, focus indicators, and meaningful icons or graphics against adjacent colors. |
| CLR-2 | MUST NOT use color as the only way to convey information. Add text, an icon, or a pattern. |
| CLR-3 | MUST reserve status colors for their meaning. `color.status.danger` is for errors and destructive actions, never decoration or emphasis. |
| CLR-4 | SHOULD use a single primary action color; use secondary and accent colors sparingly for emphasis. |
| CLR-5 | If the product supports dark mode, MUST provide a dark value for every semantic color token and meet CLR-1 in both modes. |
| CLR-6 | MAY use gradients, but only if defined as tokens in the brand book. |

---

## 5. Typography

| ID | Rule |
| --- | --- |
| TYP-1 | MUST use sizes from the type scale; no arbitrary font sizes. |
| TYP-2 | MUST NOT set any text smaller than 12 px; body text SHOULD be 16 px. |
| TYP-3 | MUST use heading levels in order (H1 → H2 → H3) without skipping levels; one H1 per page. |
| TYP-4 | SHOULD use line height of about 1.4–1.6 for body text and 1.1–1.3 for headings. |
| TYP-5 | SHOULD keep reading text to about 45–90 characters per line. |
| TYP-6 | SHOULD use at most two font families, plus a monospace font if needed. |
| TYP-7 | SHOULD use sentence case for headings, labels, and buttons unless the brand book says otherwise. |

---

## 6. Layout, spacing, and visual hierarchy

| ID | Rule |
| --- | --- |
| LAY-1 | MUST take spacing (padding, margins, gaps) from the spacing scale. |
| LAY-2 | SHOULD use a column grid: 4 columns below `breakpoint.sm`, 8 columns from `breakpoint.sm`, 12 columns from `breakpoint.lg`, with gutters from the spacing scale. |
| LAY-3 | SHOULD give each view one clear focal point and one primary action. |
| LAY-4 | SHOULD group related items by proximity: less space within a group than between groups. |
| LAY-5 | SHOULD align content to the grid and a consistent leading edge; don't center long-form text. |
| LAY-6 | SHOULD cap content width: about 1280 px for application layouts, about 65–75 characters for reading text. |
| LAY-7 | MAY use compact density if the brand book selects it; compact layouts MUST still meet RSP-3 and all accessibility rules. |

Visual hierarchy, in order of strength: size → weight → color and contrast → spacing → position. Use as few levers as needed to make the order of importance obvious.

---

## 7. Responsive behavior

| ID | Rule |
| --- | --- |
| RSP-1 | MUST work at 320 px width without horizontal scrolling, except content that needs two-dimensional scrolling (data tables, maps). |
| RSP-2 | MUST NOT depend on hover for any essential function or information. |
| RSP-3 | MUST give interactive targets at least 24 × 24 CSS px (or enough spacing around smaller ones); SHOULD use 44 × 44 px on touch-first screens. |
| RSP-4 | SHOULD design mobile-first and check at 320, 375, 768, 1024, and 1440 px. |
| RSP-5 | SHOULD adapt navigation to the screen size (for example, a menu button or bottom bar on small screens). |
| RSP-6 | SHOULD keep reading and focus order the same as visual order when layouts reflow. |
| RSP-7 | SHOULD give images and media a defined aspect ratio to prevent layout shift. |

---

## 8. Components and states

### 8.1 Component spec

Document every component with: **purpose** (and when not to use it) · **anatomy** · **variants** · **sizes** and the tokens they use · **states** (8.2) · **behavior** for keyboard, pointer, and touch · **content rules** · **accessibility notes** (role, name, focus, announcements) · **do / don't** examples.

| ID | Rule |
| --- | --- |
| CMP-1 | MUST reuse an existing component before creating a new one. A new component needs a spec and review ([`docs/customization.md`](docs/customization.md#adding-a-component)). |
| CMP-2 | MUST implement every applicable state in the state matrix (8.2). |
| CMP-3 | MUST use native semantic elements: `button` for actions, links for navigation, `label` for form fields. |
| CMP-4 | SHOULD have one primary button per view or region; other actions use secondary or tertiary styles. |
| CMP-5 | MUST ask for confirmation or offer undo before an irreversible or destructive action completes. |

### 8.2 State matrix

| State | Requirement | Applies to |
| --- | --- | --- |
| Default | Resting appearance | All |
| Hover | Subtle change; never the only cue (RSP-2) | Pointer-interactive |
| Focus-visible | Visible indicator per A11Y-3 | Keyboard-interactive |
| Active / pressed | Immediate feedback | Interactive |
| Disabled | Reduced emphasis; explain why when it isn't obvious | Controls |
| Loading | Progress indicator; prevents duplicate submission | Async actions and content |
| Selected | Distinct from hover and focus; not color alone (CLR-2) | Toggles, tabs, rows |
| Error | Message in text plus status color and icon | Inputs, forms, async content |
| Empty | Explains what belongs here and how to start | Lists, tables, search results |
| Success | Confirms the outcome | Completed actions |

### 8.3 Common components

- **Buttons:** labels start with a verb ("Save changes"). Icon-only buttons need an accessible name. A loading button keeps its width and blocks repeat clicks. Destructive buttons use `color.status.danger` and follow CMP-5.
- **Forms:** every field has a visible label. Required fields are marked in text, not only by color or an asterisk. Helper text goes before the field is used, not as placeholder text. Validate formats when the field loses focus and completeness on submit. Don't show errors before the user has interacted. On error, move focus to the first invalid field or an error summary.
- **Feedback:** choose by urgency. Inline messages for field-level issues; banners for page-level conditions; toasts for brief confirmations only. Never put critical errors in a toast, and don't auto-dismiss messages people need time to read.
- **Dialogs and drawers:** focus moves into the overlay, stays inside it while open, `Esc` closes it, and focus returns to the trigger on close. Don't stack dialogs.
- **Tables and lists:** use real table headers; right-align numbers and show units; make sortable columns and the current sort visible; design loading and empty states.

### 8.4 Loading and wait times

| Expected wait | Pattern |
| --- | --- |
| Under about 0.1 s | No indicator needed |
| About 0.1–1 s | Keep the interaction's own feedback (pressed state); avoid spinners that flash |
| About 1–10 s | Spinner for actions; skeleton matching the final layout for content |
| Over about 10 s | Progress with percentage or estimate, and a way to cancel when possible |

---

## 9. Interaction and motion

| ID | Rule |
| --- | --- |
| INT-1 | MUST give visible feedback for every user action. |
| INT-2 | MUST respect `prefers-reduced-motion`: remove or reduce non-essential motion. |
| INT-3 | MUST NOT flash content more than three times per second. |
| INT-4 | MUST NOT change context unexpectedly when an element receives focus or a value changes (no auto-submit or auto-navigation on input). |
| INT-5 | SHOULD use the motion tokens; UI transitions SHOULD take 100–300 ms. |
| INT-6 | SHOULD preserve user input after errors and when navigating back. |

---

## 10. Navigation and information architecture

| ID | Rule |
| --- | --- |
| NAV-1 | MUST show the current location: active navigation item and a visible page heading. |
| NAV-2 | MUST give every page or screen a unique, descriptive title. |
| NAV-3 | MUST keep repeated navigation in the same place and order across pages. |
| NAV-4 | MUST provide a way to skip repeated navigation (for example, a "Skip to content" link) on web pages. |
| NAV-5 | SHOULD keep top-level navigation to about seven items or fewer; group the rest. |
| NAV-6 | SHOULD use breadcrumbs when the hierarchy is deeper than two levels. |
| NAV-7 | SHOULD name navigation items with words users recognize, not internal jargon. |
| NAV-8 | SHOULD make important views linkable, with the URL reflecting state such as tabs and filters, where the platform allows. |

---

## 11. Content and UX writing

| ID | Rule |
| --- | --- |
| CNT-1 | MUST label buttons and links by their action or destination ("Download report", not "Click here"). |
| CNT-2 | MUST write error messages that say what went wrong and how to fix it, without blaming the user. |
| CNT-3 | MUST NOT use placeholder text as the only label. |
| CNT-4 | SHOULD follow the brand book's voice; fallback voice: clear, neutral, and concise. |
| CNT-5 | SHOULD use sentence case and avoid all caps for anything longer than a short label. |
| CNT-6 | SHOULD format dates, numbers, and currency for the locale in the brand book (fallback: the user's locale). |

---

## 12. Accessibility

Baseline: **WCAG 2.2 Level AA** ([W3C WCAG 2.2](https://www.w3.org/TR/WCAG22/)), or a stricter target set in the brand book. CLR-1, CLR-2, TYP-3, RSP-1, RSP-3, INT-2, INT-3, INT-4, NAV-1 to NAV-4, and CNT-3 are part of this baseline.

| ID | Rule |
| --- | --- |
| A11Y-1 | MUST meet WCAG 2.2 Level AA, or the stricter level in the brand book. |
| A11Y-2 | MUST be fully operable by keyboard, in a logical order, with no keyboard traps. |
| A11Y-3 | MUST show a visible focus indicator (at least 2 px, at least 3:1 against adjacent colors) and keep focused elements from being hidden behind sticky headers or overlays. |
| A11Y-4 | MUST give meaningful images a text alternative; decorative images get an empty alternative. |
| A11Y-5 | MUST connect labels, instructions, and error messages to their fields in code, and announce status messages to assistive technology. |
| A11Y-6 | MUST allow text resizing to 200% and increased text spacing without loss of content or function. |
| A11Y-7 | MUST expose name, role, and state for custom components; prefer native elements. |
| A11Y-8 | MUST set the page language. |
| A11Y-9 | MUST offer a single-pointer alternative to dragging and multi-point gestures. |

Notes: disabled controls are exempt from contrast minimums under WCAG, but they still need a non-color cue and, where helpful, an explanation. How to test is described in [`docs/validation.md`](docs/validation.md#how-to-test).

---

## 13. Prototyping rules

| ID | Rule |
| --- | --- |
| PRO-1 | MUST label each prototype with its fidelity and scope, for example "Interactive prototype · front-end only · fictional data". |
| PRO-2 | Mid- and high-fidelity prototypes MUST use the tokens and documented components, exactly as production UI would. |
| PRO-3 | MUST include the states that matter for the flow: at least default, empty, loading, and error, plus success where an action completes. |
| PRO-4 | MUST use fictional or anonymized content. MUST NOT include real customer, employee, or confidential data. |
| PRO-5 | SHOULD show the smallest and largest target screen sizes. |
| PRO-6 | SHOULD trace every screen to a requirement in the prototype brief ([`docs/prototyping-workflow.md`](docs/prototyping-workflow.md)). |
| PRO-7 | MUST pass the review checklist before being shared as "ready for review". |
| PRO-8 | Low-fidelity wireframes MAY skip brand styling (grayscale), but MUST be labeled as wireframes. |

---

## 14. Rules for AI-assisted generation

| ID | Rule |
| --- | --- |
| AI-1 | MUST read this file, then the brand book, then the prototype brief, before generating UI. |
| AI-2 | MUST define token values in one place (for example, a single `:root` block) and reference tokens everywhere else. |
| AI-3 | MUST NOT invent brand values (BRD-2). Use the fallbacks and list them. |
| AI-4 | MUST produce every applicable state, not just the default (CMP-2, PRO-3). |
| AI-5 | SHOULD end each response with a short report: brand fields used, fallbacks applied, rule deviations by ID, and which checklist items were verified versus still need a human check. |
| AI-6 | MUST NOT report a check as passed when it wasn't performed (for example, screen reader testing). |

---

## 15. Definition of done

A screen, component, or prototype is done when:

- every applicable MUST rule is met;
- every SHOULD deviation is documented with a reason;
- the review checklist in [`docs/validation.md`](docs/validation.md) is complete; and
- any approved deviation is recorded in the exception log.
