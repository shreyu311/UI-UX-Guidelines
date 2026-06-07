# Design tokens & Figma handoff

> **Former location:** Part II — § 5 · Tokens and § 6 · Figma Integration.
> 

## Tokens (ShadCN + Tailwind)

Use ShadCN **CSS variables** as the canonical runtime tokens.

### globals.css (:root highlights)

- `--background` = #F4F5F0
- `--foreground` = #26272A
- `--primary` = #208692
- `--ring` = #208692
- `--secondary` = #C7D8D0
- `--muted` = #CFD0BF
- `--muted-foreground` = #527779
- `--accent` = #D4D970
- `--border` = #CFD0BF
- `--radius` = 0.75rem

### Tailwind mapping (brand)

- `brand.background` / `--background` = #F4F5F0
- `brand.text` = #26272A
- `brand.primary` = #208692
- `brand.deep` = #164F5B
- `brand.accent` = #D4D970
- `brand.c1` … `brand.c4` = complementary set (see **Brand & foundations**)

### Figma variable mapping rule

The app reads **`globals.css`** (`:root`). In Figma, create **Color** variables whose names match the mapping table — each maps to exactly one CSS variable.

| Token name in Figma (use this) | Value | Code (`globals.css`) |
| --- | --- | --- |
| background | #F4F5F0 | `--background` |
| foreground | #26272A | `--foreground` |
| primary | #208692 | `--primary` |
| ring | #208692 | `--ring` |
| secondary | #C7D8D0 | `--secondary` |
| muted | #CFD0BF | `--muted` |
| muted-foreground | #527779 | `--muted-foreground` |
| accent | #D4D970 | `--accent` |
| border | #CFD0BF | `--border` |

**Radius:** Number variable `radius` = **12** (px) — same as `--radius: 0.75rem` when `1rem` = 16px.

**Brand extensions in Figma:** `deep` = #164F5B, `brand-c1` … `brand-c4` for nav/hero/marketing without raw hex drift.

## Figma integration and handoff

- **Canonical Figma link:** paste the team **design library** file URL in the CTO hub TL;DR and keep it current.
- **Variables ↔ code:** names map to ShadCN/Tailwind usage in `globals.css`.
- **Structure:** Primitives + Semantic collections if the file grows; add **modes** only for real themes.
- **Typography:** text styles match **Brand & foundations**; name for Dev Mode (e.g. `Heading / H1`, `Body / Default`).
- **Layout:** Auto layout with **8pt** spacers named `8`, `16`, `24`, `32`, `48`, `64`.
- **Components:** align variants with **Components & patterns**; new recurring patterns go in the library or are exceptions per **Governance**.
- **Elevation:** effect styles for the three shadow levels.

### Figma → implementation checklist

- [ ]  Frames use **semantic color variables** (no undocumented raw hex).
- [ ]  Spacing and type use **named styles** or variables from this system.
- [ ]  **States** designed or called out: default, hover, focus, disabled, loading, error where applicable.
- [ ]  **Touch targets** ≥ 44×44px for interactive controls.
- [ ]  **Library link** and **frame link** attached to the work item.