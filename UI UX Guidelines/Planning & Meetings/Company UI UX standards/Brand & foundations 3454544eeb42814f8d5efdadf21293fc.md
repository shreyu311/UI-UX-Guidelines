# Brand & foundations

## Relationship to brand

Link your official **brand guidelines** here. This page defines **product UI foundations** derived from brand: roles, scale, and motion — not marketing print rules.

## Color roles (semantic)

Define **roles**, not only hex values. Example set to adapt:

- **text.primary** — default body text
- **text.secondary** — supporting text
- **text.inverse** — on bold or imagery
- **surface.canvas** — page background
- **surface.panel** — cards and panels
- **border.default** — dividers and outlines
- **accent.primary** — primary actions
- **accent.danger** — destructive actions
- **focus.ring** — visible focus (must meet contrast)

**Rule:** interactive states (hover, pressed, disabled) map from the same role family.

## Typography

- **Type scale:** display, h1–h3, body, small, caption — with line-height and weight.
- **Numeric alignment:** tabular figures for tables and money.
- **Readability:** max line length ~65–75 characters for long reading (web).

## Spacing rhythm

Use a **4pt or 8pt base grid** (pick one company-wide). Spacing tokens: `space.1` (4), `space.2` (8), `space.3` (12), `space.4` (16), `space.6` (24), `space.8` (32) — adjust names to your token system.

## Elevation and shadows

- Levels for **rest, raised, overlay** — tied to z-index policy.
- Avoid deep shadows on dense data UIs; prefer borders for clarity.

## Icons and illustration

- Icon style: **outlined vs filled**, stroke width, corner radius.
- **Metaphor consistency** — do not mix metaphors for the same action.

## Motion

- Durations: **fast** (120–160ms), **medium** (200–280ms), **slow** (320–400ms) for product UI.
- Easing: standard **ease-out** for entrances; **ease-in-out** for repositioning.
- **prefers-reduced-motion:** provide non-motion equivalent (instant or opacity-only).

## Photography (in-product)

When brand uses photography in UI: aspect ratios, gradient scrims for text legibility, and consent for faces.