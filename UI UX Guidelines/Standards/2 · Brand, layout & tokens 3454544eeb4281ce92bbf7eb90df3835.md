# 2 · Brand, layout & tokens

## Brand palette & UI usage

### Source palette (HEX)

- Primary: **#208692** · Deep primary: **#164F5B** · Accent: **#D4D970**
- Complementary: **#E5EADF**, **#CFD0BF**, **#C7D8D0**, **#527779**
- Background: **#F4F5F0** · Text: **#26272A**

### Visual swatches (Figma / PNG — Apr 14 standard)

**Do not** use generated remote tiles for stakeholder sign‑off. Show **real components** on real backgrounds: paste a **Figma embed** (`Share` → copy link → paste in Notion) or a **dated PNG export** per swatch row. HEX values stay authoritative in the tables above; visuals prove **hover**, **gradient**, and **semantic** application.

<aside>
🖼️

Until each frame is linked: export from the canonical library with filenames like `palette-primary-YYYYMMDD.png` and attach here, or paste the Figma frame URL under the matching slot in **Embedded gallery** below.

</aside>

### UI usage rules

- Default background **#F4F5F0**; default text **#26272A**.
- Primary actions / focus ring: **#208692**.
- Deep surfaces (nav, headers, hero bands): **#164F5B**.
- Accent **#D4D970**: sparing highlights only — **not** a primary CTA.

### Semantic palette (errors, warnings, missing information)

- **Destructive red** (`destructive` token family, **#DC2626**) is **reserved** for: **blocking errors**, **data loss or irreversible danger**, **field-level validation failures**, and **critical alerts** that require immediate corrective action. Do **not** use red for decoration, marketing emphasis, or “brand heat.”
- **Warning / attention (#F59E0B family)** is for **non-blocking risk**, **incomplete or missing required information** before submit, **policy reminders**, and **degradable experiences** (for example stale data). Pair with concise copy and a clear next step. **Do not** use red for these—reserve red for errors and danger.
- **Success (#16A34A family)** confirms completed actions and positive system states (including success **chips**). Never use destructive red for success.
- **Info / neutral** feedback uses **muted neutrals + primary text**; keep routine information visually calm so it does not read like an error.
- **Psychology and consistency:** users associate **red with “something is wrong or unsafe.”** Primary teal (**#208692**) must **never** communicate failure or destructive outcomes.
- **Ship with visual proof in Figma:** maintain frames that show (1) field error vs (2) page-level blocking alert vs (3) “profile incomplete” style banner using **warning** tokens vs (4) inline success after save. Cross-reference **chips, alerts, and notifications** in [4 · Components & patterns](4%20%C2%B7%20Components%20&%20patterns%203454544eeb4281479040ce5bd99406c7.md).

### Do / Don't for deep primary

- **Do:** sidebar/topbar, headers, emphasis containers; keep long text readable.
- **Don't:** default page background; stack many dark surfaces.

### Gradients and shadows

- **Primary gradient:** linear **135deg**, **#164F5B → #208692** — **token-backed** (deep → primary stops only). Use on **approved** CTA bands, heroes, or marketing surfaces—not as generic decoration. Show the gradient on **real components** in Figma so usage is unambiguous.
- **No ad-hoc gradients:** do not invent new angles, stops, or rainbow blends outside this spec unless logged in `docs/design-exceptions.md`.
- **Shadows:** lv1 cards · lv2 menus · lv3 modals (exact CSS in **Shadow specs** below).

## Color usage documentation (examples)

Shipped patterns must ship with **visual documentation**: Figma frames (preferred) or exported PNGs showing **real components** on real backgrounds—not swatch-only slides.

### Minimum example set

- **Marketing / hero band:** primary gradient **#164F5B → #208692** on a CTA strip with accessible label contrast.
- **App chrome:** deep primary **#164F5B** nav or header with long-form readable foreground (verify contrast).
- **Default surface:** card on **#F4F5F0** using `border` / `muted` tokens + **shadow lv1**.
- **Primary vs secondary actions:** primary filled vs outline/secondary on the **same** surface.
- **Accent discipline:** accent **#D4D970** as highlight only—not the sole CTA fill.

### Do / Don't (documentation)

- **Do** tie every frame to **semantic variables** visible in Dev Mode (`primary`, `deep`, `accent`, `destructive`, …).
- **Don't** ship orphan hex fills or one-off gradients that are not in this chapter.

### Embedded gallery (Figma embed or PNG — required slots)

For each shipped pattern below, keep **one living frame** in the canonical Figma file **and** paste a **Figma embed** or **PNG export** under the matching callout (Apr 14 **visual-first** bar: reviewers must see components, not prose-only). Prefer embeds so hover/gradient states stay inspectable.

<aside>
🖼️

**1 · Hero / marketing CTA band** — gradient **#164F5B → #208692** on real buttons + headline. Paste link or image.

</aside>

<aside>
🖼️

**2 · App chrome** — deep nav or header with long-form text. Paste link or image.

</aside>

<aside>
🖼️

**3 · Card on background** — default surface, border, shadow lv1. Paste link or image.

</aside>

<aside>
🖼️

**4 · Primary vs secondary** — both actions on the same surface. Paste link or image.

</aside>

<aside>
🖼️

**5 · Accent discipline** — accent used as highlight, not sole CTA. Paste link or image.

</aside>

<aside>
🖼️

**6 · Semantic states** — field error, blocking alert, warning “incomplete profile” banner, inline success. Paste link or image.

</aside>

## Typography

- **Bricolage Grotesque** titles · **Inter** body · **Barlow** chrome.
- H1 40/32 · H2 32/28 · H3 28/24 · Body 16/14 · Caption 12 (desktop/mobile).
- Tailwind: `font-heading`, `font-sans`, `font-footer`.

### Product copy & imagery

Voice, **aosenuma** lowercase rule, and imagery live in **4 · Components & patterns** with accessibility guidance.

---

## Layout & grid

- **8pt** layout grid (8,16,24,32,48,64); **4pt** micro spacing inside components.
- **Touch targets** ≥ **44×44px**.

### Patterns

- **List pages:** header + CTA + filters; table vs cards; drawer vs page for details.
- **Detail pages:** summary header + grouped sections.
- **Forms:** inline validation; errors explain fix + recovery.
- **Context-specific hierarchy:** document dense admin vs marketing in Figma.

---

## Tokens & Figma handoff

### globals.css (`:root`)

Canonical keys (values must match Figma semantic vars):

- `--background` → **#F4F5F0**
- `--foreground` → **#26272A**
- `--primary` → **#208692**
- `--ring` → **#208692**
- `--secondary` → **#C7D8D0**
- `--muted` → **#CFD0BF**
- `--muted-foreground` → **#527779**
- `--accent` → **#D4D970**
- `--border` → **#CFD0BF**
- `--radius` → **0.75rem** (12px when `1rem` = 16px)

```css
:root {
  --background: #F4F5F0;
  --foreground: #26272A;
  --primary: #208692;
  --ring: #208692;
  --secondary: #C7D8D0;
  --muted: #CFD0BF;
  --muted-foreground: #527779;
  --accent: #D4D970;
  --border: #CFD0BF;
  --radius: 0.75rem;
}
```

### Tailwind brand mapping

`brand.*` mirrors the palette above; extend `deep`, `brand-c1…c4` in Figma for nav/marketing without raw hex drift.

### Figma variable table

| Token name in Figma | Value | Code (`globals.css`) |
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

**Radius (shells):** Figma semantic `radius` for **cards, modals, panels, and page shells** = **12px**, matching `--radius` **0.75rem** at a **16px** root.

**Inputs and compact controls:** text inputs, compact **select** triggers, and dense filter chips may use **8px corner radius** where specified in **Components & patterns**—tighter for form density, still token-backed, never arbitrary one-off values.

### Handoff checklist

- [ ]  Semantic variables only on production frames
- [ ]  Named styles for type/spacing
- [ ]  States designed or explicitly called out
- [ ]  Touch targets ≥ 44×44px
- [ ]  Library + frame links on tickets

<aside>
🔗

**Figma workflow + “fix now” triage** (where the canonical library URL lives, publish hygiene, detached instances, library permissions vs real UX defects): [5 · Governance & shipping](../Process%20&%20Governance/5%20%C2%B7%20Governance%20&%20shipping%203454544eeb4281808c68e067d0b6a0f7.md) → *Figma integration (workflow)*.

</aside>

---

## Shadow specs

- **Shadow 1 (soft):** `0 2px 4px rgba(0,0,0,0.05)` — cards
- **Shadow 2 (elevated):** `0 4px 12px rgba(0,0,0,0.1)` — dropdowns
- **Shadow 3 (floating):** `0 10px 24px rgba(0,0,0,0.15)` — modals

## Figma integration detail

- **Canonical library:** keep one team file URL current (link it from **1 · Scope & principles** or this chapter).
- **Variables ↔ code:** Figma names map to `globals.css` (`background`, `foreground`, `primary`, `secondary`, `muted`, `muted-foreground`, `accent`, `border`, `ring`, `radius`). Resolved HEX must match this doc — no ad-hoc fills on production frames.
- **Collections:** prefer **Primitives** + **Semantic** as the file grows; a single collection is fine early.
- **Modes:** add themes (e.g. light/dark) only when they ship; default mode matches this document.
- **Typography:** text styles mirror the scale above; name for Dev Mode (e.g. `Heading / H1`, `Body / Default`).
- **Layout:** Auto layout with spacer variables `8`, `16`, `24`, `32`, `48`, `64` aligned to engineering vocabulary.
- **Components:** interactive variants align with **4 · Components & patterns**; net-new recurring patterns belong in the library or require a logged exception.
- **Elevation:** model the three shadows as effect styles or variable-backed shadows so cards, menus, and modals stay consistent.
- **Handoff hygiene:** reviewers should see **variable names** in Dev Mode, not orphan hex. Tickets/PRs should link the Figma frame plus a small token table when helpful.

## Brand-only Figma variables

Add **Color** variables for nav/hero/marketing without raw hex drift: **`deep`** `#164F5B`, **`brand-c1`** `#E5EADF`, **`brand-c2`** `#CFD0BF`, **`brand-c3`** `#C7D8D0`, **`brand-c4`** `#527779`. Use `deep` for dark bands and pair with accessible foreground per contrast rules.