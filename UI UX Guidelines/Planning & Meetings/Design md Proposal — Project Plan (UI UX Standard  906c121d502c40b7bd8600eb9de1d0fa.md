# Design.md Proposal — Project Plan (UI/UX Standard + Agentic Design)

## Objective

Deliver a standard `design.md` template that guides AI + developers to create UI/UX components aligned to our brand book standards and the ShadCN-based implementation approach, with a repeatable rinse-and-repeat workflow (examples + process).

## Source documents (Notion references)

- Meeting driver + action items: [**UI/UX March 30th March 30, 2026 10:00 AM**](UI%20UX%20March%2030th%20@March%2030,%202026%2010%2000%20AM%203334544eeb4280f2825fec5d5e9a6f07.md)
- Mandatory UI/UX cadence + prototyping baseline (Jorge): [UI/UX Reporting Process & Prototyping Standards — Mandatory Compliance](../Process%20&%20Governance/UI%20UX%20Reporting%20Process%20&%20Prototyping%20Standards%20%E2%80%94%20%20e1a5cc1e61df4667b06403c01b3643fc.md)
- UI/UX Compliance program (4-week tracker): [UI/UX Compliance — 4-Week Plan](UI%20UX%20Compliance%20%E2%80%94%204-Week%20Plan%20b5ecedeef4614525b46f2a21904bc8aa.md)
- UI/UX Governance execution system: [5 · UI/UX governance — PM execution playbook](../Process%20&%20Governance/5%20%C2%B7%20UI%20UX%20governance%20%E2%80%94%20PM%20execution%20playbook%20e112617dc0d74306a44fe55ac121ef52.md)
- Cursor rules reference (for `.cursor/rules` structure): [Using Cursor Rules with of Mermaid Diagrams](https://www.notion.so/Using-Cursor-Rules-with-of-Mermaid-Diagrams-1ea4544eeb4280d4a08ce003a703f149?pvs=21)
- Exec Dashboard Cursor baseline example (pattern for rule files + README): [Lean MVP Plan (1)](https://www.notion.so/Lean-MVP-Plan-1-30c4544eeb4280f99766eabe034cf98a?pvs=21)
- StakeAI UI/UX plan example (ShadCN + Next.js baseline): [Lean MVP Plan — StakeAI UI/UX V1.0](https://www.notion.so/Lean-MVP-Plan-StakeAI-UI-UX-V1-0-d7f6a6f3e14248ee9553ab4d2911fef8?pvs=21)

---

## Deliverables (checkpoints)

1) `design.md` v0.1 — Template skeleton (sections + required fields)

- Exit criteria:
    - Covers brand token documentation requirements, accessibility target (WCAG 2.1 AA), interaction states, and reporting fields per the mandatory standard.[[1]](../Process%20&%20Governance/UI%20UX%20Reporting%20Process%20&%20Prototyping%20Standards%20%E2%80%94%20%20e1a5cc1e61df4667b06403c01b3643fc.md)
    - Includes a “How to use this file” section for developers.

2) `design.md` v0.2 — Filled examples (2–3 component examples)

- Exit criteria:
    - Includes prompt patterns: component creation, screen build, refactor, and acceptance checklist.
    - Shows at least: Button, Form/Input state pattern, Table/List pattern (ShadCN-aligned).

3) Developer workflow + enforcement notes

- Exit criteria:
    - Step-by-step process: where `design.md` lives, when it must be updated, and how it links to tasks/PRs.
    - Clear “definition of done” checklist for UI work (prototype gates + interaction states + a11y).

4) Review log + v1.0 final

- Exit criteria:
    - Peer review captured (incl. Vraj per meeting action item) + versioned updates.
    - v1.0 is ready to adopt across projects and aligns to the compliance cadence.[[2]](UI%20UX%20March%2030th%20@March%2030,%202026%2010%2000%20AM%203334544eeb4280f2825fec5d5e9a6f07.md)[[1]](../Process%20&%20Governance/UI%20UX%20Reporting%20Process%20&%20Prototyping%20Standards%20%E2%80%94%20%20e1a5cc1e61df4667b06403c01b3643fc.md)

---

## Project plan (phases, timeboxed)

### Phase A — Requirements extraction + template skeleton (1–2 days)

Milestone: `design.md` v0.1 skeleton ready for review

- Inputs to extract and encode:
    - Reporting requirements + evidence expectations (weekly UI/UX status fields).[[1]](../Process%20&%20Governance/UI%20UX%20Reporting%20Process%20&%20Prototyping%20Standards%20%E2%80%94%20%20e1a5cc1e61df4667b06403c01b3643fc.md)
    - Prototyping gates (lo-fi before sprint planning; hi-fi before demo/UAT).[[1]](../Process%20&%20Governance/UI%20UX%20Reporting%20Process%20&%20Prototyping%20Standards%20%E2%80%94%20%20e1a5cc1e61df4667b06403c01b3643fc.md)
    - Interaction states specification (loading/empty/error/success) + copy rules.[[1]](../Process%20&%20Governance/UI%20UX%20Reporting%20Process%20&%20Prototyping%20Standards%20%E2%80%94%20%20e1a5cc1e61df4667b06403c01b3643fc.md)
    - Accessibility baseline (WCAG 2.1 AA) + per-screen checklist.[[1]](../Process%20&%20Governance/UI%20UX%20Reporting%20Process%20&%20Prototyping%20Standards%20%E2%80%94%20%20e1a5cc1e61df4667b06403c01b3643fc.md)
    - Design token reference sheet format (colors/typography/spacing/component inventory).[[1]](../Process%20&%20Governance/UI%20UX%20Reporting%20Process%20&%20Prototyping%20Standards%20%E2%80%94%20%20e1a5cc1e61df4667b06403c01b3643fc.md)

### Phase B — Examples + workflows (2–4 days)

Milestone: `design.md` v0.2 with examples + dev usage workflow

- Build examples using the patterns already used in our ecosystem:
    - ShadCN + Tailwind-first component inventory approach.[[3]](https://www.notion.so/Lean-MVP-Plan-StakeAI-UI-UX-V1-0-d7f6a6f3e14248ee9553ab4d2911fef8?pvs=21)
    - Use the Cursor rules convention as the “developer-consumable” formatting reference.[[4]](https://www.notion.so/Using-Cursor-Rules-with-of-Mermaid-Diagrams-1ea4544eeb4280d4a08ce003a703f149?pvs=21)[[5]](https://www.notion.so/Lean-MVP-Plan-1-30c4544eeb4280f99766eabe034cf98a?pvs=21)
- Define workflows:
    - “AI component build” workflow: prompt → output → QA checklist → PR.
    - “Screen build” workflow: lo-fi → hi-fi → interaction states → a11y → handoff.

### Phase C — Review + adoption (3–5 days)

Milestone: `design.md` v1.0 adopted on 1 active project + governance hook

- Peer review session + revision pass (include Vraj).
- Adoption target:
    - Attach `design.md` to one active project’s UI/UX compliance page as the canonical reference.[[6]](UI%20UX%20Compliance%20%E2%80%94%204-Week%20Plan%20b5ecedeef4614525b46f2a21904bc8aa.md)
- Governance:
    - Add a simple audit rule: any UI task must link to prototype evidence + reference `design.md` expectations.[[1]](../Process%20&%20Governance/UI%20UX%20Reporting%20Process%20&%20Prototyping%20Standards%20%E2%80%94%20%20e1a5cc1e61df4667b06403c01b3643fc.md)

---

## Roles & accountability

- Owner (R): Shreyas — drafts and drives to closure.[[2]](UI%20UX%20March%2030th%20@March%2030,%202026%2010%2000%20AM%203334544eeb4280f2825fec5d5e9a6f07.md)
- Consult (C): Vraj + builders experienced with ShadCN-based execution (as needed).[[2]](UI%20UX%20March%2030th%20@March%2030,%202026%2010%2000%20AM%203334544eeb4280f2825fec5d5e9a6f07.md)
- Approver (A): CTO / UI governance owner (per the mandatory standard doc).[[1]](../Process%20&%20Governance/UI%20UX%20Reporting%20Process%20&%20Prototyping%20Standards%20%E2%80%94%20%20e1a5cc1e61df4667b06403c01b3643fc.md)

---

## Risks + mitigations

- Risk: “brand book” guidance is too abstract → Mitigation: convert into explicit token rules + concrete examples.
- Risk: devs don’t adopt → Mitigation: wire into UI task acceptance criteria + PR checklist.
- Risk: inconsistent AI outputs → Mitigation: standard prompt templates + validation checklist (a11y + interaction states).

---

## Next 48 hours (actionable)

- Draft `design.md` v0.1 outline and share for peer feedback (incl. Vraj).[[2]](UI%20UX%20March%2030th%20@March%2030,%202026%2010%2000%20AM%203334544eeb4280f2825fec5d5e9a6f07.md)
- Pick 2–3 components to demonstrate (ShadCN-first).
- Define the minimum acceptance checklist (prototype evidence + interaction states + WCAG baseline) as a copy/paste block in the template.[[1]](../Process%20&%20Governance/UI%20UX%20Reporting%20Process%20&%20Prototyping%20Standards%20%E2%80%94%20%20e1a5cc1e61df4667b06403c01b3643fc.md)