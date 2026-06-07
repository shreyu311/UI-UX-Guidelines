# 7 · Brand assets (logo & brandbook)

## aosenuma brand assets

Canonical home for the **logo** and the **Brandbook v1 (Oct 2023)**. Whenever any artifact (PPT, template, prototype, doc, UI) needs the aosenuma logo or theme, use the files linked here.

<aside>
📎

**How this page is used (Cursor / agent convention):** A Cursor rule (`aosenuma-brand.mdc`, `alwaysApply: true`) points every chat at the local copies of these files and to the palette below. The rule lives at `C:\Users\pc\Desktop\aosenuma-brand-assets\aosenuma-brand.mdc`. Any request to make a PPT / template / prototype will default to this theme.

</aside>

### Files

- **Logo (PNG):** local — `C:\Users\pc\Desktop\aosenuma-brand-assets\logo.png` · canonical URL — [logo_aosenuma-01.png](https://aosenuma.com/wp-content/uploads/2023/02/logo_aosenuma-01.png)
- **Brandbook (PDF):** local — `C:\Users\pc\Desktop\aosenuma-brand-assets\brandbook.pdf` (52 pp, Oct 2023)

![aosenuma logo](https://aosenuma.com/wp-content/uploads/2023/02/logo_aosenuma-01.png)

aosenuma logo

<aside>
📤

**Attach the binaries to this Notion page manually (one time).** The Notion API cannot upload raw PNG/PDF files — it can only embed URLs. Drag `logo.png` and `brandbook.pdf` from `C:\Users\pc\Desktop\aosenuma-brand-assets\` into the **Attachments** toggle below so everyone on the team can download them from Notion too.

</aside>

- 📎 Attachments (drop files here)
    
    Drop `logo.png` and `brandbook.pdf` into this toggle from Desktop → aosenuma-brand-assets.
    

---

## Logo — rules of use (brandbook p.15–19)

- The imagotipo represents four concepts: **regeneration, movement, environment, nature** — built from organic lines with variable thickness.
- **Do not** recolor, outline, skew, rotate, or redraw the logo. Use `logo.png` as-is.
- **Minimum sizes:** 2.5 × 2.5 cm (icon only) · 11.6 × 2.5 cm (full lockup).
- **Clear space:** respect the protection area around the mark (see brandbook p.17).
- The wordmark `aosenuma` is **always lowercase**, even at the start of sentences.

---

## Color palette (brandbook p.22 — authoritative hex)

| Role | Hex | RGB | Use |
| --- | --- | --- | --- |
| **Primary — Teal 700** | **#164F5B** | 22, 79, 91 | Gradient start, dark primary, hover on CTAs |
| **Primary — Teal 500** | **#208692** | 32, 134, 146 | Default primary, CTAs, links, gradient end |
| Teal complementary | #527779 | 82, 119, 121 | Secondary surfaces, muted teal |
| Accent — Lime | **#D4D970** | 212, 217, 112 | Accent only (≤ 20%); highlights, callouts |
| Paper (background) | #F4F5F0 | 244, 245, 240 | Page / slide background |
| Sage wash | #E5EADF | 229, 234, 223 | Subtle surface, hover for outlined buttons |
| Warm sand | #CFD0BF | 207, 208, 191 | Complementary surface |
| Mist | #C7D8D0 | 199, 216, 208 | Complementary surface |
| Ink (text) | #26272A | 38, 39, 42 | Primary text on paper |

**Signature gradient:** `linear-gradient(135deg, #164F5B 0%, #208692 100%)`. No decorative one-off gradients — see hub → *Gradients* rule.

---

## Typography (brandbook p.20)

| Role | Typeface | Weight | Feel |
| --- | --- | --- | --- |
| Titles / Quotes | **Bricolage Grotesque** | Regular | Humana / dinámica |
| Subtitles / Body | **Inter** | Light | Limpieza / accesible |
| Headers / Footers | **Barlow** | Regular | Elegante / legible |

---

## Voice & tone (brandbook p.13)

- Warm, close, accessible. Write in **first person plural** (*nosotros*).
- The brand name `aosenuma` is always lowercase, using the **medium** weight of the typeface.
- Example: *“Somos una consultoría de sostenibilidad estratégica y desempeño social.”*

---

## Imagery style (brandbook p.26–27)

- AI-generated imagery in **impressionist oil-paint** style, OR high-resolution close-up photography.
- Avoid faces of non-employees.
- Line-based organic iconography; wave / ocean motifs are on-brand (the mark references ocean movement).

---

## Use in new PPTs / templates / prototypes

1. **PPT / slide decks (16:9):** `#F4F5F0` background · Teal `#208692` headings · **Inter Light** body · logo bottom-right at ≥ 2.5 cm. Title slide: 135° gradient full-bleed + white-knockout logo.
2. **Templates (docs, letterhead):** Barlow headers · Inter body · full logo lockup top-left · `#26272A` text on `#F4F5F0` paper.
3. **Prototypes / UI:** follow the **semantic tokens** from the parent *UI/UX guidelines* hub — `primary = #208692`, `destructive = #DC2626`, 8 pt grid, radius 12 px, ShadCN primitives.
4. Always reference this page (and the local brandbook PDF) in the artifact's README / footer so reviewers can audit.

---

## Parent

[UI/UX guidelines](../UI%20UX%20guidelines%2020be6c5f913d4f53ac0e76eb5e904eef.md)