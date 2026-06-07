# UI/UX Reporting Process & Prototyping Standards — Mandatory Compliance

<aside>
🎨

**TO: All Project Managers**

**FROM: Jorge (CTO)**

**DATE: March 16, 2026**

**RE: Establishing a mandatory UI/UX reporting cadence and prototyping baseline across all active projects.**

</aside>

---

Team,

The [UI/UX Audit — All Active Projects (Feb 26, 2026)](https://www.notion.so/UI-UX-Audit-All-Active-Projects-Feb-26-2026-c26dcae28ba34e86b565c6fee64baf73?pvs=21) made one thing painfully clear: **no project has visual wireframes or mockups, accessibility is universally weak, and interaction states are afterthoughts.** These are not edge-case findings — they are systemic failures that affect every single project we are running.

We are not going to keep shipping specs without visual proof that the UI works. Starting now, UI/UX reporting and prototyping are **mandatory PM responsibilities** — not optional, not "nice to have," not "we'll get to it later."

This document defines the standard. Follow it.

---

## 1 · UI/UX Reporting — What You Owe and When

Every PM must include a **UI/UX status section** in their RAD log entries and weekly reporting. This is not a separate process — it is embedded into the existing cadence.

### 📋 Weekly UI/UX Status Report (Mandatory Fields)

Every Friday, as part of your EOD readiness check, you must update the following for each project:

| **Field** | **Description** | **Acceptable Evidence** |
| --- | --- | --- |
| **Prototype Status** | Current state of wireframes/mockups for each primary screen | Link to Figma, Notion embed, or exported image in project repo |
| **Screens Completed** | Count of screens with finalized lo-fi or hi-fi prototypes | Linked list of completed screens with version number |
| **Screens Remaining** | Count and names of screens still pending prototyping | Linked backlog with target completion dates |
| **Interaction States Coverage** | % of screens with loading, empty, and error states designed | Link to state definitions per screen |
| **Accessibility Compliance** | WCAG 2.1 AA checklist progress per screen | Checklist with pass/fail per criterion |
| **Open UI/UX Decisions** | Count of unresolved design decisions with owners and due dates | Decision log with status (Open/Locked) |
| **Stakeholder Sign-off** | Which screens have been reviewed and approved by the project lead or client | Sign-off record with date and reviewer name |

<aside>
🛑

**Rule:** If your weekly report does not include the UI/UX status section, your report is **incomplete** and will be flagged by the Steward PM. No exceptions.

</aside>

---

## 2 · Prototyping Standards — The Minimum Bar

Every project must have prototypes that meet the following baseline **before entering active development of any screen**. Building UI without a prototype is building blind.

### Phase 1: Lo-Fi Wireframes (Required Before Sprint Planning)

- **Every primary screen** must have a lo-fi wireframe before any development task is created for that screen.
- Lo-fi wireframes must show:
    - [x]  **Layout structure** — content blocks, navigation, and key interaction zones
    - [x]  **Information hierarchy** — what the user sees first, second, third
    - [x]  **Data placeholders** — realistic sample data, not "Lorem ipsum"
    - [x]  **Navigation flow** — how the user gets to and from this screen
    - [x]  **Responsive breakpoints** — at minimum, desktop (1440px) and tablet (1024px) layouts
- **Tool:** Figma, Excalidraw, or Notion-embedded sketches. The tool does not matter — the output does.
- **Naming convention:** `[Project]-WF-[ScreenName]-v[X.X]` (e.g., `StakeAI-WF-GraphExplorer-v0.1`)

### Phase 2: Hi-Fi Prototypes (Required Before Client Demo or UAT)

- **Every client-facing screen** must have a hi-fi prototype before it is shown to a client or enters UAT.
- Hi-fi prototypes must include:
    - [x]  **Brand-compliant design tokens** — colors, typography, spacing from the project's design system
    - [x]  **All interaction states** — loading (skeleton), empty (CTA + illustration), error (message + retry), success (confirmation)
    - [x]  **Real copy** — actual labels, placeholders, error messages, and tooltips in the project's primary language
    - [x]  **Component specifications** — padding, margin, font size, color hex values annotated for developer handoff
    - [x]  **Clickable flow** — at minimum, the primary happy-path user journey must be interactive
- **Naming convention:** `[Project]-HF-[ScreenName]-v[X.X]` (e.g., `Woodside-HF-CaseDetail-v1.0`)

<aside>
⚠️

**Gate rule:** No development task for a screen may be marked "In Progress" unless a lo-fi wireframe exists and is linked in the task's acceptance criteria. No screen may enter UAT or client demo without a hi-fi prototype.

</aside>

---

## 3 · Interaction States — Design Them, Don't Imply Them

The audit found that **every project** mentions interaction states but none have visual designs for them. This ends now.

For **every screen** in your project, you must define and design the following four states:

| **State** | **What It Covers** | **Required Deliverable** |
| --- | --- | --- |
| **Loading** | Skeleton screens, progress indicators, shimmer effects | Visual mockup showing skeleton layout matching the screen's content structure |
| **Empty** | First-run experience, no-data states, zero-result search | Visual mockup with illustration/icon + descriptive copy + primary CTA |
| **Error** | API failures, validation errors, timeout, permission denied | Visual mockup with error message copy + retry action + fallback guidance |
| **Success** | Confirmation of completed actions (save, submit, delete, export) | Visual mockup or toast/banner pattern with confirmation copy |

### Copy Standards for States

- Error messages must be **human-readable** — no raw error codes, no "Something went wrong."
- Empty states must include a **call to action** — tell the user what to do next, not just that there is nothing to see.
- All copy must be written in the **project's primary language** (e.g., Spanish for Woodside).
- Copy must be stored in an **i18n-ready string table** within the project repository.

---

## 4 · Accessibility — WCAG 2.1 AA Is the Floor, Not the Ceiling

Effective immediately, **WCAG 2.1 AA** is the mandatory accessibility target for all projects. This is non-negotiable.

### Minimum Accessibility Checklist (Per Screen)

- [x]  **Color contrast:** All text meets 4.5:1 ratio (normal text) or 3:1 (large text) against background
- [x]  **No color-only indicators:** Every status badge, RAG indicator, or severity tag includes a text label or icon alongside color
- [x]  **Keyboard navigation:** Every interactive element is reachable and operable via keyboard (Tab, Enter, Escape, Arrow keys)
- [x]  **Focus indicators:** Visible focus ring on all interactive elements
- [x]  **ARIA roles:** Key components (modals, dropdowns, tabs, data tables) have appropriate ARIA roles and labels
- [x]  **Alt text:** All images, icons, and charts have descriptive alt text
- [x]  **Form labels:** Every input field has an associated label (not just placeholder text)
- [x]  **Touch targets:** Minimum 44×44px for all clickable elements (especially for mobile-first projects like Woodside)

<aside>
📌

**How to validate:** Use Chrome DevTools Lighthouse audit (Accessibility score ≥ 90) and manual keyboard walkthrough. Document results in the project's QA section.

</aside>

---

## 5 · Design System Governance — One Organization, One System

The audit identified that multiple projects define design tokens independently despite sharing shadcn/ui + Tailwind. This creates visual inconsistency and duplicated effort.

### Mandatory Design Token Documentation (Per Project)

Every project must maintain a **Design Token Reference Sheet** within its project repository that includes:

- [x]  **Color palette** — hex values, CSS variable names, and usage rules (primary, secondary, accent, semantic/status)
- [x]  **Typography scale** — font families, sizes, weights, and line heights for headings, body, captions, labels
- [x]  **Spacing scale** — padding and margin values used across components
- [x]  **Component inventory** — list of all shadcn/ui components used, with any customizations documented
- [x]  **Brand-specific overrides** — any project-specific tokens that differ from the aosenuma base palette

### Cross-Project Alignment

- All internal-facing projects (StakeAI, Executive Dashboard, RapdAI, AI PMO) must use the **aosenuma brand tokens** (teal/lime palette, Bricolage Grotesque + Inter + Barlow).
- Client-facing projects (Woodside) use the **client's brand guide** but must still document tokens in the same format.
- Any new component not in shadcn/ui must be **documented with specs** before use and shared across projects where applicable.

---

## 6 · Prototyping Cadence — Integrated Into the Existing PM Operating System

Prototyping is not a side activity. It is embedded into the existing delivery cadence.

### How This Maps to Existing Processes

| **Existing Process** | **UI/UX Addition** | **Owner** |
| --- | --- | --- |
| **Lean MVP Pre-Kickoff (Gate 1)** | Lo-fi wireframes for all primary screens must exist before Gate 1 sign-off | PM + Designer |
| **Task Database (Gate 2)** | Every UI task must link to its corresponding wireframe in acceptance criteria | PM |
| **RAD Log Daily Update** | Include prototype progress and any blocked UI/UX decisions | PM |
| **Steward Daily Compliance Report** | Steward flags projects with missing or stale prototypes | Steward PM |
| **Friday EOD Readiness Check** | UI/UX status section completed (see Section 1) | PM |
| **Monday PM Meeting** | Review prototype completion rates as part of Forecast vs. Actuals | Steward PM |
| **QA Gates** | Accessibility checklist must pass before UAT entry | PM + QA |

---

## 7 · The Minimum UI/UX Package — Copy/Paste Checklist

For every project you own, you must be able to check **every single box** below. If you cannot, your UI/UX compliance is incomplete and your project is at risk.

- [x]  **Lo-fi wireframes:** All primary screens have wireframes with layout, hierarchy, data placeholders, navigation flow, and responsive breakpoints
- [x]  **Hi-fi prototypes:** All client-facing screens have brand-compliant, interactive prototypes with real copy and component specs
- [x]  **Interaction states:** Loading, empty, error, and success states designed for every screen with human-readable copy
- [x]  **Accessibility:** WCAG 2.1 AA checklist completed per screen — contrast, keyboard nav, ARIA roles, focus indicators, touch targets
- [x]  **Design tokens:** Design Token Reference Sheet maintained with colors, typography, spacing, component inventory
- [x]  **API contracts:** Frontend-backend contracts locked with request/response schemas, error codes, and pagination
- [x]  **Open decisions:** All UI/UX decisions logged with owner, due date, and status (Open/Locked) — zero overdue items
- [x]  **Weekly reporting:** UI/UX status section included in every Friday EOD report

<aside>
📌

**How to use this checklist:** Duplicate Section 7 as your project's UI/UX compliance tracker. Update it weekly. When all boxes are checked, your project meets the minimum UI/UX standard.

</aside>

---

## 8 · What Happens Next

**By end of day Friday, March 20, 2026**, every active project must have:

1. **Lo-fi wireframes** for at least the top 3 primary screens — linked in the project repository.
2. **Interaction states** documented for at least 1 primary screen as a reference pattern for the rest.
3. **WCAG 2.1 AA** declared as the accessibility target in the project card.
4. **Design Token Reference Sheet** created (even if partially filled) and linked from the project card.
5. **UI/UX status section** added to the next RAD log update.

This is not aspirational. This is your deadline.

---

## 9 · The Point You Are Missing

Prototypes are not deliverables for designers. They are **risk mitigation tools for PMs.** A prototype:

- Prevents costly rework by catching layout and interaction problems **before code is written.**
- Aligns developer implementation with PM expectations **without ambiguity.**
- Gives clients something tangible to react to **before the demo.**
- Creates an audit trail that proves the PM **thought through the user experience** before shipping.

The audit showed that every project is building from text specs alone. Text specs are necessary but insufficient. You need **visual proof** that the UI works before you build it.

> 👉 **Prototyping is not extra work — it is the work that prevents the most expensive rework.** A wireframe that takes 2 hours to create prevents 2 weeks of post-demo redesign.
> 

Get it together. I will be reviewing each project's UI/UX compliance personally starting March 21.

**Jorge**