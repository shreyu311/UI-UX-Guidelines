# 3 · Style Card for UI/UX

## Brand color palette (canonical)

These HEX values match **2 · Brand, layout & tokens** and **`globals.css`**. Use semantic variables in shipped UI—not one-off fills.

<aside>

**[YOUR_PRIMARY]** `primary` · `ring`

</aside>

<aside>

**[YOUR_PRIMARY_DARK]** `deep`

</aside>

<aside>

**[YOUR_ACCENT]** `accent`

</aside>

<aside>

**[YOUR_BACKGROUND]** `background`

</aside>

<aside>

**[YOUR_TEXT]** `foreground`

</aside>

<aside>

**[YOUR_COMPLEMENTARY_3]** `muted-foreground`

</aside>

<aside>

**[YOUR_COMPLEMENTARY_1]** `border` · `muted`

</aside>

<aside>

**[YOUR_COMPLEMENTARY_2]** `secondary`

</aside>

### Semantic colors (feedback)

**Success #16A34A** · **Warning #F59E0B** · **Error / destructive #DC2626** · **Disabled #D1D5DB** (with **#9CA3AF** text where specified).

#### Visual proof (Figma embed or PNG)

Replace generated tiles with **Figma embeds** or **dated PNGs** showing these tokens on **real controls** (chips, alerts, validation). Keep in sync with **2 · Brand, layout & tokens** → *Embedded gallery*.

<aside>
🖼️

**Attach or embed:** success chip/toast, warning banner, destructive dialog primary button, disabled form control — each on `background` / `foreground` surfaces.

</aside>

## Embedded pattern gallery (Apr 14 — mirror Brand)

Use the **same six documentation slots** as [2 · Brand, layout & tokens](2%20%C2%B7%20Brand,%20layout%20&%20tokens%203454544eeb4281ce92bbf7eb90df3835.md) so posters and product spec stay aligned. Paste **Figma** or **PNG** per callout.

<aside>
🖼️

**1 · Hero / marketing CTA band** — gradient **[YOUR_PRIMARY_DARK] → [YOUR_PRIMARY]** on real buttons + headline.

</aside>

<aside>
🖼️

**2 · App chrome** — deep nav or header with long-form text.

</aside>

<aside>
🖼️

**3 · Card on background** — default surface, border, shadow lv1.

</aside>

<aside>
🖼️

**4 · Primary vs secondary** — both actions on the same surface.

</aside>

<aside>
🖼️

**5 · Accent discipline** — accent as highlight, not sole CTA.

</aside>

<aside>
🖼️

**6 · Semantic states** — field error, blocking alert, warning “incomplete profile” banner, inline success.

</aside>

[[YOUR_COMPANY_NAME] Components Reference — design.md v1.0.pdf](3%20%C2%B7%20Style%20Card%20for%20UI%20UX/[YOUR_COMPANY_NAME]_Components_Reference__design.md_v1.0.pdf)

## Components overview + button anatomy

This sheet introduces the [YOUR_COMPANY_NAME] component system and the baseline button anatomy (8pt grid), including Large/Medium/Small sizes and the 44×44px minimum touch target.

![[YOUR_COMPANY_NAME] Components Reference — design.md v1.0-images-0.jpg](3%20%C2%B7%20Style%20Card%20for%20UI%20UX/[YOUR_COMPANY_NAME]_Components_Reference__design.md_v1.0-images-0.jpg)

## Button state matrix — pressed & processing (primary + split)

Reference for how primary buttons behave in pressed and processing/loading states across contained/outlined/text/split variants, using the token palette (primary + deep primary).

![[YOUR_COMPANY_NAME] Components Reference — design.md v1.0-images-1.jpg](3%20%C2%B7%20Style%20Card%20for%20UI%20UX/[YOUR_COMPANY_NAME]_Components_Reference__design.md_v1.0-images-1.jpg)

## Controls + input/select sizing and states

Guidance for form controls (checkbox, radio, switch, chips) and input fields: focus ring uses primary; error uses destructive; select/dropdown sizing and open-menu behavior are shown.

![[YOUR_COMPANY_NAME] Components Reference — design.md v1.0-images-2.jpg](3%20%C2%B7%20Style%20Card%20for%20UI%20UX/[YOUR_COMPANY_NAME]_Components_Reference__design.md_v1.0-images-2.jpg)

## Dropdown menu spec callout (compliance targets)

Quick reference for dropdown menu compliance (item height, padding, and elevation/shadow) so implementation matches the design system consistently.

![[YOUR_COMPANY_NAME] Components Reference — design.md v1.0-images-3.jpg](3%20%C2%B7%20Style%20Card%20for%20UI%20UX/[YOUR_COMPANY_NAME]_Components_Reference__design.md_v1.0-images-3.jpg)

## Cards, containers, and spacing grid

Defines card variants (basic/elevated/deep surface), container sizing (modal/drawer/card), default radii/shadows, and the spacing scale aligned to the 8pt grid (with 4pt micro-adjustments).

![[YOUR_COMPANY_NAME] Components Reference — design.md v1.0-images-4.jpg](3%20%C2%B7%20Style%20Card%20for%20UI%20UX/[YOUR_COMPANY_NAME]_Components_Reference__design.md_v1.0-images-4.jpg)