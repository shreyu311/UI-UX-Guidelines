# 4 · Components & patterns

## Component system (ShadCN)

- ShadCN by default; theme tokens + variants; avoid one-off CSS; composition over forks.

## Coverage (all shipped UI primitives)

Together with **Scope & principles** and **Brand, layout & tokens**, this chapter defines rules for **actions**, **forms and selection**, **navigation**, **feedback**, **data display**, **overlays**, and **layout**. Missing guidance here is **missing spec**, not optional styling—extend the doc or log a temporary deviation in `docs/design-exceptions.md`.

## Density & product context

Different product surfaces need different **information density** without inventing new hex. Label every major frame with one of the rows below so reviewers know which rhythm to apply.

| Context | Type scale & rhythm | Spacing rhythm | Information density | When to use | Required Figma template frames |
| --- | --- | --- | --- | --- | --- |
| **Default (product app)** | Standard **H1–caption** scale from **2 · Brand**; body **16/14** desktop/mobile. | **8pt** layout grid; **4pt** micro inside controls; comfortable section gaps (**24–32px**). | Balanced; prioritize scannability over raw rows per screen. | Most signed-in workflows, settings, mixed marketing + app chrome. | Maintain an empty **“Template · Default · 1440”** frame in the canonical library (auto-layout shell + placeholder content regions). |
| **Marketing / storytelling** | Larger display headings; more **Bricolage**; generous line-height for hero copy. | More **48–64px** vertical rhythm between sections; fewer controls per row. | Low density; fewer KPIs visible above the fold; emphasis on narrative and primary CTA. | Landing pages, campaign surfaces, hero bands using the **approved primary gradient**. | **“Template · Marketing · 1440”** frame with hero, primary/secondary CTAs, and accent callouts only where spec allows. |
| **Admin / dashboards** | Same tokens, tighter vertical rhythm; may step down one text size for tables and metadata. | Prefer **16–24px** gutters inside dense tables; keep **8pt** alignment for chrome. | Higher density; more rows, filters, and secondary actions visible without scrolling. | Internal tools, operator consoles, KPI-heavy dashboards, large data tables. | **“Template · Admin · 1440”** frame with dense table + filter bar + drawer slot; document default row heights here and in Figma. |

**Figma expectation:** each template row above should exist as a **named starter frame** in the canonical library—even as empty placeholders—so “dashboard vs marketing card” reviews do not become ad-hoc pixel hunts.

### Out of scope (unless adopted as product UI)

**One-off marketing microsites**, **print**, and **unthemeable third-party embeds**; document intentional exceptions if they appear in product.

See the **UI element inventory** (category → elements → guideline location) in [1 · Scope & principles](1%20%C2%B7%20Scope%20&%20principles%203454544eeb42810c89b3d3e4ef563c43.md).

### Core color palette (canonical HEX)

Use **semantic variables** in Figma and code (`primary`, `deep`, `background`, …). Full rules, gradients, and semantics: [2 · Brand, layout & tokens](2%20%C2%B7%20Brand,%20layout%20&%20tokens%203454544eeb4281ce92bbf7eb90df3835.md).

#### Visual swatches (Figma / PNG — Apr 14)

**Do not** ship review feedback against generated remote tiles. Use **Figma embeds** or **dated PNG exports** for palette + state proof; keep the **token callouts** below as the quick numeric reference.

<aside>
🖼️

**Mirror** the six documentation slots in [2 · Brand, layout & tokens](2%20%C2%B7%20Brand,%20layout%20&%20tokens%203454544eeb4281ce92bbf7eb90df3835.md) (*Embedded gallery*) so Components, Brand, and Style Card stay aligned.

</aside>

<aside>

**#208692** `primary` · `ring`

</aside>

<aside>

**#164F5B** `deep`

</aside>

<aside>

**#D4D970** `accent`

</aside>

<aside>

**#F4F5F0** `background`

</aside>

<aside>

**#26272A** `foreground`

</aside>

<aside>

**#527779** `muted-foreground`

</aside>

<aside>

**#CFD0BF** `border` · `muted`

</aside>

<aside>

**#C7D8D0** `secondary`

</aside>

<aside>

**#16A34A** success

</aside>

<aside>

**#F59E0B** warning

</aside>

<aside>

**#DC2626** destructive / error

</aside>

<aside>

**#D1D5DB** disabled surfaces

</aside>

### Buttons (ShadCN variants)

- **Primary:** solid **primary** background with **white** label/icon — main actions.
- **Secondary:** **outline** using complementary border tones; label/icon in **deep primary** — secondary actions.
- **Ghost / tertiary:** transparent background — low-emphasis actions.
- **Destructive:** solid **destructive** red (ShadCN default) — irreversible/dangerous actions; never use primary teal for failure.
- States: default · hover · focus-visible · pressed · disabled · loading · selected when applicable.
- **Padding:** document horizontal + vertical padding per variant for Dev Mode; prefer **8pt-grid** values (e.g. **32px** horizontal per side for large CTAs). Default large CTAs to **32px** horizontal padding unless an exception is filed. **Teaching note (Apr 14):** demos sometimes cite **30px** — **snap to 32px** unless a **logged exception**.
- **Touch targets:** interactive hit area stays **≥ 44×44px** (may require invisible hit slop beyond the visual button).
- Heights: Large **48px**, Medium **40px**, Small **32px**.

### Matrices (token-aligned)

- Primary: default **#208692** · hover **#164F5B** · pressed **#145A66** · loading spinner on **#208692**.
- Destructive: **#DC2626** / **#B91C1C** / **#991B1B**; disabled **#D1D5DB** text **#9CA3AF**; soft **#FEE2E2** / **#FECACA**.
- Secondary (outline): border muted neutrals; label/icon **deep primary**; hover uses light wash **`#E5EADF`** with border discipline from Figma.
- Ghost / text: transparent default; hover/pressed washes **`#E5EADF`** / **`#C7D8D0`** per variant—never imply error with red.

### Authoritative button state matrix (color + interaction)

Reference labels **Contained / Outlined / Text** map to ShadCN **primary / secondary / ghost**. **Split** buttons: follow the **Split buttons** section below; primary segment uses **primary** colors, menu trigger uses **secondary** or **ghost**—still document per screen in Figma for edge cases.

| Variant | Default | Hover | Pressed | Focus-visible | Disabled | Loading | Selected / toggle (if used) |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Primary (Contained) | Fill **#208692**, label **white** | Fill **#164F5B** | Fill **#145A66** | **#208692** ring (`--ring`) | Fill **#D1D5DB**, label **#9CA3AF** | Spinner on **#208692** fill | Use **deep** fill or muted wash—define per component in library |
| Secondary (Outlined) | Border muted, label **#164F5B** | Background **#E5EADF** | Background **#C7D8D0** | **#208692** ring | Border/label muted **#D1D5DB** / **#9CA3AF** | Spinner on transparent or light wash | Border + background emphasis per pattern |
| Ghost (Text) | Transparent, label **#164F5B** | Background **#E5EADF** | Background **#C7D8D0** | **#208692** ring | Label **#9CA3AF** | Spinner adjacent to label | Light selected wash without heavy fill |
| Destructive (Contained / Outlined / Text) | Fill or border **#DC2626** per variant | **#B91C1C** (fill) / **#FEE2E2** (soft surfaces) | **#991B1B** / **#FECACA** | Visible ring using token-backed focus | Muted neutrals as primary disabled | Spinner on destructive fill | Avoid destructive toggles unless explicitly designed |

### Button sizing and spacing

- **Heights:** Large **48px**, Medium **40px**, Small **32px**.
- **Padding:** prefer **8pt grid**; large CTAs default **32px** horizontal padding per side unless an exception is filed.
    - **Teaching note (Apr 14):** workshop examples sometimes cite **30px** side padding for illustration — **snap to 32px** on the **8pt** grid unless a **logged exception** in `docs/design-exceptions.md` documents why a non-grid value ships.
- **Touch target:** minimum interactive target **≥ 44×44px** — extend hit slop beyond the visible shape when necessary.

### Controls & inputs

- Checkbox/radio selected: **#208692**; switch active: **#208692**; inactive uses muted neutrals.
- **Chips:** Primary **#208692**, Success **#16A34A**, Error **#DC2626**, Warning **#F59E0B**, Disabled **#D1D5DB**.
- Inputs: focus **#208692**; errors **destructive**; **default input corner radius 8px** on **`#FFFFFF`** fields (dense controls); dropdown rows **36px** tall, **12px** padding, **shadow lv2**.

### Forks

Document rationale, deltas, usage sites, and maintenance risk in the PR when deviating from ShadCN baseline.

### Platform-specific patterns

- **Scope discipline:** keep **one org-wide SSOT**; document only patterns shared across products (skip one-off widgets in this standard).
- **Maps / heavy data viz:** only when the product needs them; use complementary teals/greys for series so semantic reds stay reserved.
- **Custom components:** when something recurs (complex tables, dashboards, bespoke nav), define shared anatomy + states here and in Figma.

### Fork documentation checklist

If you fork ShadCN, capture in-repo and in the PR description:

- Why the fork was required
- What changed from baseline
- Where it is used (screens/components)
- Risk/maintenance notes (what breaks on upstream updates)

## Navigation & shell

### Primary app navigation

- **Persistent nav** (side or top) uses **deep (#164F5B)** for the bar; active item uses **primary** or **white-on-deep** only after a **contrast check** on labels and icons.
- **Mobile:** collapse into sheet or drawer (**shadow lv3**, **12px** corners on the sheet container unless full-bleed). Provide a **single clear entry** (menu icon) with **≥ 44×44px** hit target.
- **Depth:** one clearly **primary** navigation model per app (do not stack unrelated primary nav systems).

### Tabs and secondary navigation

- Tabs switch **within the same context** (same record, same object). **Do not** use tabs for cross-area navigation that should live in primary nav.
- **Active tab:** **primary** underline or **deep** bottom border; **never** use **destructive** red for “selected.”
- **Overflow:** if more than **about seven** tabs would crowd the bar, use scroll, overflow menu, or split into **sections**—do not shrink text below readable minimum.

### Breadcrumbs and page headers

- **Breadcrumbs** for admin or **depth ≥ 3**; marketing pages may omit when the hierarchy is intentionally flat.
- **Page header** bundles title (semantic **H1**), optional metadata, and **primary actions** aligned to the **8pt** grid; stack vertically on small breakpoints with actions after the title block.

### Complex navigation (mega-menu, multi-column, command palette)

- **Mega-menu / large flyout:** max **three** columns; **shadow lv2**; **Escape** closes and returns focus to the trigger; include a **skip link** pattern on dense admin pages where applicable.
- **Command palette (⌘K style):** treat as a **modal** (focus trap, **lv3** shadow); group commands; **destructive** actions require a **second step** or typed confirmation.
- **Icon rail + expanded nav:** icon-only rails require **tooltips** and **accessible names** (`aria-label` where needed); always expose an **expand** affordance for discoverability.

## Data display & visualization

### Tables and dense lists

- Prefer **token** backgrounds (**#FFFFFF** rows on **#F4F5F0**); optional muted zebra using **muted** / **border** tokens—never red striping except true error row state.
- **Sticky headers** may use **#FFFFFF** with **shadow lv1** divider; sort affordances use **muted-foreground** token, active sort **primary**.
- **Numeric columns** right-align; **status** uses **semantic chips** (see **Controls & inputs**) instead of raw colored text without meaning.

### KPI tiles and sparklines

- Structure: **label · value · change**. Positive business change may use **success** green; negative business change uses **foreground** or **muted** unless the metric is literally a **blocking error** (then **destructive** is allowed with copy that explains risk).
- **Sparklines** should draw series with **primary**, **brand-c4 (#527779)**, **secondary**, and **muted** before introducing new hues. Reserve **red** for series that mean **failure/threshold breach**, and label that meaning in the legend.

### Charts and maps (in-product)

- **Categorical color order:** **#208692 → #527779 → #C7D8D0 → #CFD0BF → #164F5B** before adding new colors. Avoid **#DC2626** except for **error** or **danger** series.

#### Chart series swatches (visual order — Figma / PNG)

Embed a **single chart frame** showing series **1 → 5** in order (**#208692 → #527779 → #C7D8D0 → #CFD0BF → #164F5B**) on a real plot—not numbered placeholder tiles.

<aside>
🖼️

Paste **Figma** or a **PNG** of a categorical chart using the sequence above; label each series in the legend so **red** stays reserved for failure/danger semantics.

</aside>

- **Legends** are mandatory when more than one series is shown; provide a **data table** or accessible alternative when the chart is the primary insight.
- **Maps:** prefer **sequential teal/grey ramps** for fills; pins for incidents use **warning**/**error** tokens per severity—not **accent** yellow for danger.
- **Loading and failure:** charts show **skeleton** or compact placeholder; maps show **loading** state and a **recoverable error** with retry—align with **Required states** below.

## Split buttons

- **Layout:** primary **Contained** segment on the **left**; menu trigger on the **right** uses **secondary outline** or **ghost**; **8px** gap on the **8pt** grid between segments.
- **Trigger size:** chevron / overflow control is **≥ 32×32px** visual, **≥ 44×44px** hit target when space allows.
- **Menu:** **shadow lv2**, row height **36px**, **12px** horizontal padding—same as **select** menus.
- **States:** each segment has independent **hover / pressed / disabled**; open menu sets **`aria-expanded="true"`** on the trigger.
- **Destructive entries** in the menu use **destructive** row styling and require **confirmation** before irreversible work.

## Overlays: focus management

- **Modals:** trap focus while open; **Escape** closes unless edits would be lost—then confirm. On close, return focus to the element that opened the dialog (preserve Radix/ShadCN default unless a documented exception).
- **Drawers:** same **focus trap** and **Escape** behavior; background content should be **inert** for assistive tech when the drawer is modal.
- **Nested overlays:** avoid; if unavoidable, **last opened closes first** and focus returns to the previous layer’s logical opener.
- **Initial focus:** place on the first meaningful control or the dialog title region per content; document the choice on the Figma frame for wizards with many fields.

---

## Product UI styleguide (visual poster)

<aside>
🖼️

Replace hero image with final PNG from Figma (or `aosenuma-ui-styleguide-poster.png` from `assets`).

</aside>

### Foundations (swatches)

<aside>

**#208692** `primary` · `ring`

</aside>

<aside>

**#164F5B** `deep`

</aside>

<aside>

**#D4D970** `accent`

</aside>

<aside>

**#F4F5F0** `background`

</aside>

<aside>

**#26272A** `foreground`

</aside>

<aside>

**#527779** `muted-foreground`

</aside>

<aside>

**#CFD0BF** `border` · `muted`

</aside>

<aside>

**#C7D8D0** `secondary`

</aside>

### Type · spacing · radius · elevation

<aside>
🔤

**Headline** Bricolage · **Body** Inter · **Chrome** Barlow

</aside>

<aside>
↔

**Space** 4–64 · **Radius** 0–pill · **Default** 12px

</aside>

<aside>
🌫️

**Shadow** lv1 cards · lv2 menus · lv3 modals

</aside>

### Components (poster rows)

<aside>

**Buttons** — primary · secondary · ghost · destructive + states

</aside>

<aside>

**Inputs** — search · error · select

</aside>

<aside>

**Alerts** — ok · info · warn · error

</aside>

<aside>

**Chips** · **Tabs** (active = teal) · **Cards**

</aside>

- Implementation detail pointers
    
    See **2 · Brand, layout & tokens** for the Figma variable table, typography, gradients/shadows, and semantic palette rules.
    

## Required states

Every screen/component defines **loading**, **empty**, **error**, and **success**.

### Minimum behaviors

- **Loading:** avoid layout shift where possible; prefer skeletons for structured layouts.
- **Empty:** explain why it is empty and the next action (plus CTA when relevant).
- **Error:** include a recovery path (retry, fix inputs, contact support) — not blame-only copy.
- **Success:** confirm the action and what happens next (toast/banner as appropriate).

### Pattern examples

- Dashboard: KPI cards + table + drawer.
- Table + filters + drawer with empty/error/loading.
- Form: inline validation + disabled submit until valid + success toast.

## Worked examples

### Example 1 — Dashboard

- **Goal:** KPI overview + recent activity.
- **Pattern:** KPI cards + data table + **detail drawer** for row drill-down; include loading skeletons for cards/table and an empty state when no data yet.

### Example 2 — Table + filters + drawer

- **Goal:** searchable, filterable dataset.
- **Pattern:** filter bar + table + **empty / error / loading** row states; row opens **drawer** for preview, separate page only for deep edits.

### Example 3 — Form

- **Goal:** create or edit a record.
- **Pattern:** inline validation, disabled submit until valid, destructive confirmation if edits are risky, **success toast** after save.

## Notifications (toast vs banner)

- **Toast:** transient confirmations; do not stack endlessly — cap concurrent toasts and avoid toasts for expected outcomes users initiate.
- **Banner:** persistent system issues or policy notices users must see until dismissed or resolved.
- **Inline:** field-level validation and recoverable errors beside the control.

---

## Content & UX writing

- Warm, accessible tone; **aosenuma** always lowercase.
- Default voice: first-person plural where appropriate ("We…").
- **Buttons:** verb-first labels (`Invite teammate`, `Download report`); avoid vague **OK** / **Submit** when a specific verb works.
- **Links:** describe the destination; avoid **click here**.
- **Dates / numbers / currency:** follow active user locale; store canonical formats in the backend as your architecture requires.
- Imagery: AI impressionist oil style; real photos high-res close-ups; no external faces.
- Errors: what happened + how to fix + how to recover (ties to **chapter 1** checklist).

---

## Accessibility

- **Target:** meet **WCAG 2.1 Level AA** expectations for customer-facing UI unless legal requires stricter.
- Full keyboard paths including dialogs/menus; visible **focus** using the **primary** color (same as **`--ring`** in `globals.css`) — never remove focus outlines without a token-backed replacement.
- Semantic structure (headings, labels, `aria` where needed); meaningful contrast on text and critical icons (**4.5:1** for normal text as a rule of thumb).
- Images: meaningful **alt** text; decorative images marked decorative.
- Motion: respect **`prefers-reduced-motion`** for non-essential animation.
- Document `focus-visible` behavior in Figma for every interactive component.

---

## Research & usability

- Use NN/g + Material as baselines; validate risky flows (money, permissions, deletes).
- Heuristic reviews against **chapter 1** principles; lightweight usability (3–5 tasks) for new modules.
- Capture context, task, success criteria, severity, owner — always link Figma frames + token tables in tickets.