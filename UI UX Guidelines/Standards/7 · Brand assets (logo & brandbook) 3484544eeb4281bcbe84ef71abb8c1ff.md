# 7 · Brand assets (logo & brandbook)

Canonical home for your **logo** and **brandbook**. Whenever any artifact (PPT, template, prototype, doc, UI) needs your company logo or theme, use the files in [`assets/`](../../../assets/) and values in [`BRANDBOOK.md`](../../../BRANDBOOK.md).

## Files

| Asset | Path | Notes |
| --- | --- | --- |
| Logo (PNG) | `assets/logo.png` | Transparent background recommended |
| Brandbook (PDF) | `assets/brandbook.pdf` | Optional — your full brand guidelines |
| Favicon | `assets/favicon.ico` | Optional |

Replace placeholder files with your company's actual brand assets after forking this template.

## Logo rules

- Do not recolor, outline, skew, rotate, or redraw the logo.
- Define minimum size and clear space per your brandbook.
- Use the logo file as-is from `assets/logo.png`.

## Color palette

All color values are defined in [`BRANDBOOK.md`](../../../BRANDBOOK.md). Do not hardcode hex in this chapter — reference tokens:

- `primary` / `primary-dark` — CTAs, links, nav
- `accent` — highlights only (≤ 20%)
- `background` / `surface` / `text` — surfaces and typography
- Semantic tokens (`destructive`, `success`, `warning`, `info`) — see BRANDBOOK

## Typography

All typeface choices are defined in [`BRANDBOOK.md`](../../../BRANDBOOK.md).

## Voice & tone

All voice guidelines are defined in [`BRANDBOOK.md`](../../../BRANDBOOK.md).

## Branding rule (binding)

Every artifact created using this guidelines library — prototypes, decks, templates, exported PDFs — must carry **your company branding by default**:

- [ ] Logo placed per logo rules above
- [ ] Brand palette from `BRANDBOOK.md` — no off-brand accents
- [ ] Typography from `BRANDBOOK.md`
- [ ] Surface treatment matching the Style Card proof
- [ ] Footer / metadata with company name where the format supports it

Unbranded output is a defect, not a draft.
