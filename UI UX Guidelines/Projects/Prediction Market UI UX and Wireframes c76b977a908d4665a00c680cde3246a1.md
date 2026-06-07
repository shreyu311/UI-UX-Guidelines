# Prediction Market UI/UX and Wireframes

- Toolchain decision: **Stitch (confirmed)**
- Review hub for Jorge (must include links/exports + change log + gaps)
- Last updated: **2026-03-31 17:05 ET**

## Jorge package (single-page)

1) Canonical prototype (Stitch): [https://stitch.withgoogle.com/preview/9779729415150906015?node-id=56f42087f00f4ecb9bac636767e5847c](https://stitch.withgoogle.com/preview/9779729415150906015?node-id=56f42087f00f4ecb9bac636767e5847c)

2) Canonical artifacts folder (PDFs + prior UI package): [Prediction Market](https://www.notion.so/Prediction-Market-3144544eeb4280e3901adae4708222fe?pvs=21)

3) UI/UX remediation tracker (cross-project): [UI/UX Audit — Action Plan & Remediation Tracker (Mar 13, 2026)](https://www.notion.so/UI-UX-Audit-Action-Plan-Remediation-Tracker-Mar-13-2026-ca78a32a8f514db5bcfbc4cc46f54943?pvs=21)

4) What changed since last review: see **What changed since last review** below

5) What is still missing: see **Still missing / gaps** below

- Owner(s): @Shreyas Shirke @Vraj Patel
- Goal: Align on UI/UX direction, screen coverage, and review package

---

## 1) Prototype (canonical)

- Link: [Prediction Market Using Stitch](https://stitch.withgoogle.com/preview/9779729415150906015?node-id=56f42087f00f4ecb9bac636767e5847c)

---

## Prototype screens (latest upload)

- Home / Landing
    
    ![screen.png](Prediction%20Market%20UI%20UX%20and%20Wireframes/screen.png)
    

---

## Prototype screens (latest upload)

- Markets list
    
    ![screen.png](Prediction%20Market%20UI%20UX%20and%20Wireframes/screen%201.png)
    

---

## Prototype screens (latest upload)

- Market detail
    
    ![screen.png](Prediction%20Market%20UI%20UX%20and%20Wireframes/screen%202.png)
    

---

## Prototype screens (latest upload)

- Edge analysis / recommendation
    
    ![screen.png](Prediction%20Market%20UI%20UX%20and%20Wireframes/screen%203.png)
    

---

## Prototype screens (latest upload)

- Position builder
    
    ![screen.png](Prediction%20Market%20UI%20UX%20and%20Wireframes/screen%204.png)
    

---

## Prototype screens (latest upload)

- Portfolio tracking
    
    ![screen.png](Prediction%20Market%20UI%20UX%20and%20Wireframes/screen%205.png)
    

---

## 2) Wireframes (canonical)

- Hi-fi wireframe spec (component + interaction level):
    - Visual system: dark-first, 8pt spacing, 12px card radius
    - Core navigation: top app bar (logo/search/alerts/profile) + bottom nav (Home/Markets/Portfolio)
    - Shared components: market row, probability chip, edge badge, chart card, sticky CTA bar
    - States: loading skeletons, empty states w/ CTA, inline error + retry
    - Screen modules:
        - Home: opportunities carousel + watchlist module
        - Markets list: tabs + sticky filter chips + sortable list rows
        - Market detail: chart + key metrics grid + context cards + sticky actions
        - Edge analysis: setup → running stepper → results (recommendation + breakdown)
        - Position builder: direction toggle + stake presets/custom → confirm → success/failure
        - Portfolio: summary tiles + positions list + adjust flow + empty/loading/error
- Frames covered (high level):
    - Home / Landing
    - Markets list
    - Market detail
    - Edge analysis / recommendation
    - Position builder
    - Portfolio tracking

---

## Wireframe coverage (detailed)

- Home / Landing: default, search, empty, loading/error
- Markets list: default, filters/tabs, search/empty, loading/error
- Market detail: detail + chart/metrics, context cards, loading/error
- Edge analysis: pre-run, running, result, failure/insufficient data
- Position builder: direction toggle, stake presets/custom, confirm, success/failure, track-in-portfolio
- Portfolio: summary, positions list, adjust flow, empty, loading/error
- TBD (if needed): settings/profile, notifications

---

## 3) Export package (reviewable)

- PDF export (upload/link): See attached PDFs on [Prediction Market](https://www.notion.so/Prediction-Market-3144544eeb4280e3901adae4708222fe?pvs=21)
- PNG set (upload/link): Not available as a single export set yet (Stitch-based wireframes); use the **Prototype screens (latest upload)** sections above + export PNGs from Stitch if needed.
- HTML export files:
    
    [homecode.html](Prediction%20Market%20UI%20UX%20and%20Wireframes/code.html)
    
    [markets-listcode.html](Prediction%20Market%20UI%20UX%20and%20Wireframes/code%201.html)
    
    [market-detailcode.html](Prediction%20Market%20UI%20UX%20and%20Wireframes/code%202.html)
    
    [edge-analysiscode.html](Prediction%20Market%20UI%20UX%20and%20Wireframes/code%203.html)
    
    [position-buildercode.html](Prediction%20Market%20UI%20UX%20and%20Wireframes/code%204.html)
    
    [porfoliocode.html](Prediction%20Market%20UI%20UX%20and%20Wireframes/code%205.html)
    
    [code.html](Prediction%20Market%20UI%20UX%20and%20Wireframes/code%206.html)
    

---

## What changed since last review (latest)

- Toolchain decision locked to **Stitch** (no Figma dependency for wireframes/prototype).
- Canonical review package now centralized: prototype + PDFs + tracker links are all on this page.
- Strategic direction updated per Jorge’s latest directives (Phase ordering + edge definition). Source: [Strategic Directives for Prediction Market Tool](https://www.notion.so/Strategic-Directives-for-Prediction-Market-Tool-d495a0dfb15c412298d24d5ac3fbf02b?pvs=21)

---

## Tracker pointers

- Primary remediation tracker for UI/UX completeness (cross-project, includes wireframes + API contracts + states): [UI/UX Audit — Action Plan & Remediation Tracker (Mar 13, 2026)](https://www.notion.so/UI-UX-Audit-Action-Plan-Remediation-Tracker-Mar-13-2026-ca78a32a8f514db5bcfbc4cc46f54943?pvs=21)
- Design notes
    
    [DESIGN.md](Prediction%20Market%20UI%20UX%20and%20Wireframes/DESIGN.md)
    

---

## 6) Approval / next steps

- [ ]  Confirm prototype direction (UI + flow)
- [ ]  Confirm wireframe scope coverage
- [ ]  Confirm export package is sufficient for engineering handoff

[Pilot Output — Prediction Market UI/UX (Stitch screens + core components)](Prediction%20Market%20UI%20UX%20and%20Wireframes/Pilot%20Output%20%E2%80%94%20Prediction%20Market%20UI%20UX%20(Stitch%20scr%205db59aa8d3564be48cd230672972eae6.md)