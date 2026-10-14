# Example: a filled-in brand book and how it's applied

This walkthrough uses **Harbor Notes**, a fictional note-taking app invented for this example. It isn't a real company or product, and the values below are only illustrations. Contrast ratios were calculated with the WCAG formula.

---

## 1. An excerpt of the brand book

`brandbook/brandbook.md` (excerpt):

| Field | Value |
| --- | --- |
| Brand name | Harbor Notes |
| Description | A note-taking app for people who keep notes for a small team |
| Product type | Web app, desktop and mobile browsers |
| Locale | en-US |
| Accessibility target | WCAG 2.2 AA |
| Personality | Calm, plain, encouraging |
| Casing | Sentence case |
| Dark mode | Not supported |

| Role | Light value | Maps to |
| --- | --- | --- |
| Primary | `#6D28D9` | `color.action.primary`, `color.focus.ring` |
| Primary hover | `#5B21B6` | `color.action.primary.hover` |
| Text on primary | `#FFFFFF` | `color.text.on-action` |
| Accent | `#F59E0B` | `color.accent.highlight` (a brand-only token) |
| Page background | `#FAFAF9` | `color.surface.default` |
| Secondary surface | `#F5F5F4` | `color.surface.subtle` |
| Body text | `#1C1917` | `color.text.default` |
| Secondary text | `#57534E` | `color.text.muted` |
| Status colors | *(left as placeholders)* | fallbacks |
| Control border | *(left as a placeholder)* | fallback |

| Foreground | Background | Ratio | Passes for |
| --- | --- | --- | --- |
| `#1C1917` | `#FAFAF9` | 16.74:1 | Text |
| `#57534E` | `#FAFAF9` | 7.30:1 | Text |
| `#6D28D9` | `#FAFAF9` | 6.80:1 | Text, links, focus ring |
| `#FFFFFF` | `#6D28D9` | 7.10:1 | Button text |
| `#FFFFFF` | `#5B21B6` | 8.98:1 | Button text on hover |
| `#F59E0B` | `#FAFAF9` | 2.06:1 | **Decoration only**: fails as text and as a control boundary |
| `#1C1917` | `#F59E0B` | 8.14:1 | Dark text on an accent fill |

Typography: Atkinson Hyperlegible for headings and body (SIL Open Font License), falling back to the system sans-serif stack. Logo: none yet.

Constraints and exceptions:

| Constraint | Reason | Rule affected |
| --- | --- | --- |
| The accent is used only as a background fill behind `#1C1917` text, or as decoration | Fails contrast as text (2.06:1) | CLR-1 |

---

## 2. How the framework resolves it

| Token | Value used | Source |
| --- | --- | --- |
| `color.action.primary` | `#6D28D9` | Brand book |
| `color.text.default` | `#1C1917` | Brand book |
| `color.surface.default` | `#FAFAF9` | Brand book |
| `color.accent.highlight` | `#F59E0B` | Brand book, restricted to fills and decoration |
| `color.border.control` | `#737373` (4.54:1 on `#FAFAF9`) | Fallback, `DESIGN.md` §3.4 |
| `color.status.success` / `.warning` / `.danger` / `.info` | `#15803D` / `#B45309` / `#B91C1C` / `#0369A1` (4.80:1 to 6.19:1 on `#FAFAF9`) | Fallbacks |
| `font.family.sans`, `font.family.heading` | `"Atkinson Hyperlegible", system-ui, sans-serif` | Brand book plus fallback stack |
| `radius.*`, `space.*`, `shadow.*`, `duration.*` | Core scales | Fallbacks, `DESIGN.md` §3.5 |
| Logo | The text "Harbor Notes" set in the heading font | No logo provided, so none is invented (BRD-2) |
| Dark mode | Not produced | Brand book says it isn't supported |

The fallback status colors were designed for white backgrounds, so they were re-checked against this brand's off-white background; all still pass 4.5:1.

---

## 3. Asking an AI assistant for a prototype

```text
You are building an interactive prototype.

Follow DESIGN.md for the rules and brandbook/brandbook.md for brand values.
MUST rules override everything. Never invent brand values: use the fallbacks
in DESIGN.md sections 3.4 and 3.5 and list each one you used.

Task: a "Share note" dialog. A user enters a teammate's email address, picks
"Can view" or "Can edit", and shares. Show these states: default, invalid
email, sending, failed to send, and shared successfully. Use fictional
sample data only.

Deliver one token block, the dialog in every state, and a report of brand
fields used, fallbacks applied, rule deviations by ID, and which checklist
items you verified versus which need a human check.
```

---

## 4. What a good report looks like

The format below is what `DESIGN.md` AI-5 asks for. The content is illustrative.

```text
Brand fields used: brand name, primary, primary hover, text on primary,
  surfaces, text colors, accent (fill only), typography.
Fallbacks applied: color.border.control, all status colors, radius,
  spacing, shadow, and motion scales; no logo (brand name shown as text).
Deviations: none.
Verified in the code: token block defined once (AI-2); all five states
  present (AI-4); labels connected to fields (A11Y-5); dialog focus
  handling implemented (8.3).
Needs a human check: screen reader announcement of "Shared" (A11Y-5);
  200% zoom (A11Y-6); keyboard walkthrough (A11Y-2).
```

The report keeps "verified" and "needs a human check" apart, so nothing untested is presented as passing (AI-6).
