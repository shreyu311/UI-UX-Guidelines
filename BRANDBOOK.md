# Brandbook — customize for your company

This file is the **single source of truth for your brand identity**. Every other document in this repository references the tokens defined here. Replace all `[PLACEHOLDER]` values with your company's actual brand specifications.

---

## Company identity

| Field | Placeholder | Your value |
| --- | --- | --- |
| Company name | `[YOUR_COMPANY_NAME]` | |
| Tagline | `[YOUR_TAGLINE]` | |
| Logo file | `assets/logo.png` | Place your logo in `assets/` |
| Brandbook PDF | `assets/brandbook.pdf` | Optional — attach your full brand guidelines |

---

## Color palette

Define your brand colors below. Semantic UI tokens map to these values.

### Brand colors

| Token | Role | Hex | Usage |
| --- | --- | --- | --- |
| `primary` | Primary default | `[#000000]` | CTAs, links, focus rings |
| `primary-dark` | Primary hover / deep | `[#000000]` | Hover states, nav, headers |
| `accent` | Accent highlight | `[#000000]` | Sparingly — callouts, badges |
| `background` | Page background | `[#FFFFFF]` | Default surface |
| `surface` | Card / panel background | `[#FFFFFF]` | Elevated surfaces |
| `text` | Primary text | `[#000000]` | Body copy, headings |
| `text-muted` | Secondary text | `[#000000]` | Captions, placeholders |

### Semantic colors (typically consistent across companies)

| Token | Hex | Usage |
| --- | --- | --- |
| `destructive` | `#DC2626` | Errors, irreversible actions |
| `success` | `#16A34A` | Confirmations |
| `warning` | `#F59E0B` | Non-blocking risk |
| `info` | `#3B82F6` | Informational notices |
| `disabled-fill` | `#D1D5DB` | Disabled backgrounds |
| `disabled-text` | `#9CA3AF` | Disabled text |

### Signature gradient

`linear-gradient(135deg, [PRIMARY_DARK] 0%, [PRIMARY] 100%)`

---

## Typography

| Role | Typeface | Weight |
| --- | --- | --- |
| Display / Titles | `[YOUR_DISPLAY_FONT]` | Regular |
| Body | `[YOUR_BODY_FONT]` | Regular |
| Mono / Code | `[YOUR_MONO_FONT]` | Regular |

---

## Logo rules

- Do not recolor, outline, skew, rotate, or redraw the logo.
- Define minimum size and clear space per your brandbook.
- Place on title slide / cover frame + smaller mark on subsequent pages.

---

## Voice & tone

| Attribute | Your guideline |
| --- | --- |
| Personality | `[e.g. warm, professional, approachable]` |
| Pronoun | `[e.g. we, you]` |
| Company name casing | `[e.g. Title Case]` |

---

## Layout tokens

| Token | Value |
| --- | --- |
| Grid unit | `8px` |
| Spacing scale | `4 / 8 / 16 / 24 / 32 / 48 / 64` |
| Border radius | `12px` |
| Touch target minimum | `44 x 44 px` |
| Button heights | `48 / 40 / 32 px` |

---

## How to use

1. Fill in every placeholder with your company values.
2. Add logo and brandbook PDF to `assets/`.
3. Update DESIGN.md with resolved hex values.
4. Search the repo for `[YOUR_` and `[#000000]` placeholders.
