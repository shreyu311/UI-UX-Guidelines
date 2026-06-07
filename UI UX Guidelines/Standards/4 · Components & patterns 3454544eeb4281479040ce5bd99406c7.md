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

Use **semantic variables*