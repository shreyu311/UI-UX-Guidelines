# Brand book: [YOUR BRAND NAME]

> **How to fill this in**
> - Copy this file to `brandbook/brandbook.md` and edit the copy; leave the template unchanged.
> - Replace each `[PLACEHOLDER]` with your value. Leave a placeholder in place if you haven't decided; the neutral fallback from [`DESIGN.md`](../DESIGN.md) §3.4–3.5 is used and the gap is reported.
> - "Maps to" shows the token each value controls. Don't rename tokens here.
> - Examples in *italics* are fictional and only show the expected format.
> - Brand values can never override MUST rules in `DESIGN.md`. See [`README.md`](README.md#when-a-brand-value-breaks-a-must-rule) for what to do when one would.

| Field | Value |
| --- | --- |
| Brand book version | `[VERSION]` *(e.g. 0.1)* |
| Owner | `[OWNER NAME OR ROLE]` |
| Last updated | `[YYYY-MM-DD]` |

---

## 1. Brand and product context

| Field | Your value | Notes |
| --- | --- | --- |
| Brand name | `[YOUR BRAND NAME]` | Exact spelling and casing |
| One-line description | `[WHAT THE PRODUCT DOES, FOR WHOM]` | *e.g. A planning app for small volunteer groups* |
| Product type and platforms | `[WEB APP / MARKETING SITE / MOBILE / DESKTOP]` | |
| Target audience | `[PRIMARY USERS AND THEIR CONTEXT]` | Who, where, on what devices |
| Primary user tasks | `[TOP 3 TASKS]` | What people come to do |
| Locale and language | `[LOCALE, e.g. en-US]` | Drives date, number, and currency formats (CNT-6) |
| Accessibility target | `[WCAG 2.2 AA (minimum) or stricter]` | Can only be raised, not lowered (A11Y-1) |

## 2. Personality and voice

| Field | Your value |
| --- | --- |
| Personality (3–5 adjectives) | `[ADJECTIVES]` *(e.g. calm, plain, encouraging)* |
| We sound like | `[DESCRIPTION]` |
| We never sound like | `[DESCRIPTION]` |
| Point of view | `[e.g. "we" for the product, "you" for the user]` |
| Casing | `[SENTENCE CASE (default) / TITLE CASE]` for headings and buttons |
| Words we prefer | `[TERM → INSTEAD OF]` |
| Words we avoid | `[TERMS]` |
| Example: button label | `[EXAMPLE]` *(e.g. "Save changes")* |
| Example: error message | `[EXAMPLE]` *(e.g. "Enter a date after today.")* |

## 3. Color palette

### 3.1 Brand colors

| Role | Light value | Dark value | Maps to | Usage restrictions |
| --- | --- | --- | --- | --- |
| Primary | `[PRIMARY COLOR]` | `[PRIMARY COLOR, DARK MODE]` | `color.action.primary`, `color.focus.ring` | `[e.g. actions and links only]` |
| Primary hover / pressed | `[PRIMARY HOVER COLOR]` | `[PRIMARY HOVER COLOR, DARK MODE]` | `color.action.primary.hover` | |
| Text on primary | `[ON-PRIMARY TEXT COLOR]` | `[ON-PRIMARY TEXT COLOR, DARK MODE]` | `color.text.on-action` | Must pass 4.5:1 on primary |
| Secondary (optional) | `[SECONDARY COLOR]` | `[SECONDARY COLOR, DARK MODE]` | your own component tokens | `[RESTRICTIONS]` |
| Accent (optional) | `[ACCENT COLOR]` | `[ACCENT COLOR, DARK MODE]` | your own component tokens | `[e.g. highlights only, never text]` |
| Gradient (optional) | `[GRADIENT DEFINITION]` | `[GRADIENT, DARK MODE]` | your own component tokens | Only gradients defined here may be used (CLR-6) |

### 3.2 Neutrals

| Role | Light value | Dark value | Maps to |
| --- | --- | --- | --- |
| Page background | `[BACKGROUND COLOR]` | `[BACKGROUND COLOR, DARK MODE]` | `color.surface.default` |
| Secondary surface | `[SUBTLE SURFACE COLOR]` | `[SUBTLE SURFACE COLOR, DARK MODE]` | `color.surface.subtle` |
| Body text | `[TEXT COLOR]` | `[TEXT COLOR, DARK MODE]` | `color.text.default` |
| Secondary text | `[MUTED TEXT COLOR]` | `[MUTED TEXT COLOR, DARK MODE]` | `color.text.muted` |
| Disabled text | `[DISABLED TEXT COLOR]` | `[DISABLED TEXT COLOR, DARK MODE]` | `color.text.disabled` |
| Divider | `[DIVIDER COLOR]` | `[DIVIDER COLOR, DARK MODE]` | `color.border.subtle` |
| Control border | `[CONTROL BORDER COLOR]` | `[CONTROL BORDER COLOR, DARK MODE]` | `color.border.control` (needs 3:1) |

### 3.3 Status colors

Leave these as placeholders to use the tested fallbacks.

| Role | Light value | Dark value | Maps to |
| --- | --- | --- | --- |
| Success | `[SUCCESS COLOR]` | `[SUCCESS COLOR, DARK MODE]` | `color.status.success` |
| Warning | `[WARNING COLOR]` | `[WARNING COLOR, DARK MODE]` | `color.status.warning` |
| Danger | `[DANGER COLOR]` | `[DANGER COLOR, DARK MODE]` | `color.status.danger` |
| Info | `[INFO COLOR]` | `[INFO COLOR, DARK MODE]` | `color.status.info` |

### 3.4 Dark mode

`[SUPPORTED / NOT SUPPORTED]`. If supported, every color above needs a dark value (CLR-5).

### 3.5 Contrast results

Record the measured ratio for each pair you use (CLR-1: 4.5:1 for text, 3:1 for large text and UI boundaries).

| Foreground | Background | Ratio | Passes for |
| --- | --- | --- | --- |
| `[COLOR]` | `[COLOR]` | `[RATIO]` | `[TEXT / LARGE TEXT / UI ONLY / DECORATION ONLY]` |

## 4. Typography

| Role | Font family | Fallback stack | Weights | Maps to |
| --- | --- | --- | --- | --- |
| Headings | `[HEADING FONT FAMILY]` | `[FALLBACK STACK]` | `[WEIGHTS]` | `font.family.heading` (falls back to `font.family.sans`) |
| Body | `[BODY FONT FAMILY]` | `[FALLBACK STACK]` | `[WEIGHTS]` | `font.family.sans` |
| Code (optional) | `[MONO FONT FAMILY]` | `[FALLBACK STACK]` | `[WEIGHTS]` | `font.family.mono` |

| Field | Your value |
| --- | --- |
| Font source and license | `[e.g. self-hosted, open license; licensed for web use]` |
| Type scale | `[USE CORE SCALE (default) / CUSTOM SCALE: SIZES AND LINE HEIGHTS]` |
| Letter-case and emphasis rules | `[e.g. no all-caps headings; bold for emphasis, not italics]` |

## 5. Logo and brand assets

| Field | Your value |
| --- | --- |
| Logo files | `[FILES IN brandbook/assets/, e.g. logo.svg, logo-mark.svg]` or `[NONE YET]` |
| Variants | `[FULL / MARK / MONOCHROME]` |
| Minimum size | `[MINIMUM WIDTH OR HEIGHT]` |
| Clear space | `[RULE, e.g. the height of the mark on all sides]` |
| Allowed backgrounds | `[BACKGROUNDS]` |
| Never | `[e.g. recolor, stretch, rotate, add effects]` |
| Imagery style | `[PHOTOGRAPHY / ILLUSTRATION GUIDANCE]` |
| Icon set | `[ICON LIBRARY OR STYLE, e.g. outline icons, 1.5 px stroke]` |

If no logo is provided, prototypes show the brand name in plain text instead of an invented mark (BRD-2).

## 6. Spacing, layout, and density

| Field | Your value | Maps to |
| --- | --- | --- |
| Spacing base unit | `[4 PX (default) / 8 PX]` | `space.*` |
| Density | `[COMFORTABLE (default) / COMPACT]` | LAY-7 |
| Maximum content width | `[WIDTH]` | LAY-6 |
| Grid preference | `[CORE GRID (default) / CUSTOM]` | LAY-2 |

## 7. Shape, depth, and motion

| Field | Your value | Maps to |
| --- | --- | --- |
| Corner radius style | `[SQUARE / SUBTLE / ROUNDED / PILL]` or exact values | `radius.*` |
| Control radius | `[VALUE]` | `radius.md` |
| Card and dialog radius | `[VALUE]` | `radius.lg` |
| Border width | `[VALUE]` | `border.width.default` |
| Shadows | `[NONE / SUBTLE (default) / PRONOUNCED]` or exact values | `shadow.*` |
| Motion personality | `[MINIMAL / STANDARD (default)]`, within 100–300 ms (INT-5) | `duration.*`, `easing.*` |

## 8. Component conventions

| Component | Your convention |
| --- | --- |
| Buttons | `[SHAPE, CASING, ICON PLACEMENT]` |
| Inputs | `[OUTLINED / FILLED, LABEL POSITION]` |
| Cards | `[BORDER / SHADOW / BOTH]` |
| Navigation | `[TOP BAR / SIDEBAR / BOTTOM BAR ON MOBILE]` |
| Data visualization palette | `[ORDERED SERIES COLORS, each distinguishable without color alone]` |
| Other | `[COMPONENT: CONVENTION]` |

## 9. Accessibility requirements beyond the baseline

`[e.g. AAA contrast for body text; captions on all video; plain-language reading level]` or `[NONE BEYOND WCAG 2.2 AA]`

## 10. Reference screens

| Reference | Location | What it demonstrates |
| --- | --- | --- |
| `[NAME]` | `[LINK OR brandbook/assets/ FILE]` | `[e.g. preferred dashboard layout]` |

Only reference designs you created or are allowed to share.

## 11. Constraints and exceptions

| Constraint or exception | Reason | Rule affected | Approved by |
| --- | --- | --- | --- |
| `[e.g. accent color used for fills only]` | `[e.g. fails contrast as text]` | `[RULE ID, e.g. CLR-1]` | `[NAME OR ROLE]` |

Exceptions for a single screen or release belong in [`templates/exception-log.md`](../templates/exception-log.md) instead.
