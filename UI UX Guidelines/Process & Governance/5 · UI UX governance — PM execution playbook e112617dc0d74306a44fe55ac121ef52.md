# 5 · UI/UX governance — PM execution playbook

**Type:** Operational Playbook · **Effective:** 16th March · **Review Deadline:** March 20, 2026 · **Owners:** @Shreyas Shirke, @Vraj Patel

---

# 1 · Executive Summary

All 4 active projects (Executive Dashboard, Woodside, StakeAI, RapdAI) ship specs without visual validation. Zero projects have wireframes, none declare WCAG 2.1 AA, and interaction states are text-only or missing. The CTO mandate requires strict UI/UX compliance by the March 20 review.

This document converts the 8-phase compliance plan into an **executable system**: daily actions, weekly reporting cadences, hard gates that block sprint progression, and a 7-day action plan to reach minimum compliance. PMs copy-paste the reporting template into RAD logs every Friday. The Steward PM enforces gates at Monday meetings. Non-compliant projects cannot enter build phase. The goal is not perfection — it is **verifiable minimum standards** (wireframes exist, WCAG declared, interaction states spec'd, tokens defined) before any code ships.

---

# 2 · PM Execution Workflow

## Daily Actions (≤15 min)

| **Action** | **Output** | **Tool** |
| --- | --- | --- |
| Check wireframe progress against sprint plan | Updated screen count in personal tracker | Notion task database |
| Flag any new UI/UX blocker discovered during dev standup | Blocker logged in RAD log with owner + due date | RAD log |
| Verify any resolved UI/UX decision is updated from "Open" to "Locked" | Decision tracker updated | Decision tracker table |

## Required artifacts (new baseline)

- `design.md` (UI/UX Standard): [UI/UX guidelines](../UI%20UX%20guidelines%2020be6c5f913d4f53ac0e76eb5e904eef.md)
- `design-exceptions.md` (Exception log): [4 · UI/UX exceptions log — approved deviations](4%20%C2%B7%20UI%20UX%20exceptions%20log%20%E2%80%94%20approved%20deviations%2042cc3261a0d84faaaf6420c0061d7f71.md)

## PR enforcement (non-negotiable)

- Every UI PR must include the PR snippet from `design.md` (filled out).
- Any deviation from `design.md` requires an approved entry in `design-exceptions.md`.
- If no deviations: PR must explicitly state “Exceptions filed: None”.

## Weekly Actions

### Monday PM Meeting (Steward PM facilitates)

| **Agenda Item** | **Duration** | **Output** |
| --- | --- | --- |
| UI/UX Compliance Roll-Call — each PM states wireframe count, interaction states %, WCAG status | 5 min | Verbal status captured in meeting notes |
| Blockers & Escalations — any UI/UX blocker older than 3 days is escalated | 5 min | Escalation assigned to Jorge or CTO |
| Decision Lock Review — any decision past due date is force-escalated | 3 min | Overdue decisions assigned resolution owner + 48hr deadline |
| Gate Check — Steward PM confirms which projects pass/fail current gate | 2 min | Gate status recorded in RAD log |

### Friday EOD Readiness Check (Each PM, before 5:00 PM EST)

| **Action** | **Deadline** | **Failure Condition** |
| --- | --- | --- |
| Submit UI/UX status section in RAD log (use template in Section 3) | Friday 5:00 PM | Missing submission = auto-flag at Monday meeting |
| Update wireframe links in project task database | Friday 5:00 PM | Tasks without wireframe links cannot move to "In Progress" |
| Log all open UI/UX decisions with owner + due date | Friday 5:00 PM | Unowned decisions = escalation to Jorge |
| Update interaction states coverage % | Friday 5:00 PM | 0% coverage after Gate 1 = project flagged |

## Gate-Based Milestones

| **Gate** | **Name** | **Entry Criteria (ALL must pass)** | **Failure Action** |
| --- | --- | --- | --- |
| **G0** | Spec Approval | ✅ UI/UX audit completed · ✅ Scorecard assessment done · ✅ Systemic gaps documented | Spec rejected — PM must complete audit before proceeding |
| **G1** | Wireframe Sign-off | ✅ Lo-fi wireframes for top 3 screens exist · ✅ Each wireframe has layout grid + sample data + responsive notes · ✅ Naming convention followed | **Build cannot start.** Project stays in Spec phase. Escalation to Jorge if blocked >48hr. |
| **G2** | Interaction & A11y Ready | ✅ ≥1 reference screen has all 4 states (Loading/Empty/Error/Success) · ✅ WCAG 2.1 AA declared · ✅ Per-screen a11y checklist created · ✅ Design token sheet exists with hex values | **Dev tickets for UI screens are blocked.** Cannot assign UI tasks to engineers until G2 passes. |
| **G3** | Build Readiness | ✅ All G1 + G2 criteria met · ✅ All open UI/UX decisions have owners + due dates · ✅ Zero overdue decisions · ✅ RAD log UI/UX section submitted for 2 consecutive weeks | **Sprint planning excludes UI tasks.** PM must remediate before next sprint. |
| **G4** | Ship Readiness | ✅ Hi-fi prototypes for all primary screens · ✅ Lighthouse score ≥ 90 · ✅ All a11y checklist items verified · ✅ Stakeholder sign-off from Jorge | **Release blocked.** Must pass all items before deploy. |

---

# 3 · UI/UX Weekly Report Template

<aside>
📋

**Copy-paste this into your RAD log every Friday. Fill in the values for your project.**

</aside>

```markdown
## UI/UX Status — [Project Name]
Date: [YYYY-MM-DD] | PM: [Your Name] | Gate: G[0/1/2/3/4]

### Prototype Status
- Status: [Not Started / In Progress / Complete]
- Screens with wireframes: [X] of [Y]
- Screens remaining: [Y - X]
- Wireframe links: [URL or "pending"]

### Interaction States
- Coverage: [X]% ([N] of [M] primary screens have all 4 states)
- States spec'd this week: [list screens]
- States remaining: [list screens]

### Accessibility
- WCAG 2.1 AA declared: [Yes / No]
- Per-screen a11y checklist: [Created / Not Created]
- Lighthouse score: [XX / Not Run]

### Design Tokens
- Token sheet exists: [Yes / No]
- Hex values defined: [Yes / Partial / No]
- Missing tokens: [list or "none"]

### Open Decisions
| Decision | Owner | Due | Status |
|----------|-------|-----|--------|
| [Decision 1] | [Name] | [Date] | [Open/Locked] |
| [Decision 2] | [Name] | [Date] | [Open/Locked] |

### Blockers
- [Blocker 1 — owner — age in days]
- [Blocker 2 — owner — age in days]
- [None]

### Stakeholder Sign-off: [Pending / Approved]
```

### Template Usage Rules

1. **Every field is mandatory.** "N/A" is not an acceptable value — if something is not started, write "Not Started."
2. **Wireframe links must be real URLs.** "Will add later" is a failure.
3. **Open decisions with no owner are auto-escalated** to Jorge at the next Monday meeting.
4. **Blockers older than 3 days** without a resolution plan trigger CTO escalation.
5. **The Steward PM reviews all 4 project submissions** before Monday meeting and prepares a 1-line status per project.

---

# 4 · Prototyping Acceptance Criteria

## Lo-Fi Wireframe Acceptance Criteria

Every wireframe must pass ALL of the following before it is accepted:

| **#** | **Criterion** | **Pass Condition** | **Fail Example** |
| --- | --- | --- | --- |
| LF-1 | Layout grid defined | Zones are named, dimensions specified (px or %), gap values included | "The page has a header and some content" (no dimensions) |
| LF-2 | Component inventory | Every UI element listed with type (Card, Table, Badge, etc.) and placement zone | "There are some cards" (no specifics) |
| LF-3 | Realistic sample data | Data placeholders use real-looking values ("$2.4M", "John Smith", "REQ-2026-0042") | "Lorem ipsum" or "Data goes here" |
| LF-4 | Navigation flow | Click targets documented — what happens on click/tap for every interactive element | "User can navigate" (no specifics) |
| LF-5 | Responsive breakpoints | Desktop (1440px) and tablet (1024px) behavior documented for every zone | "Will be responsive" (no details) |
| LF-6 | Naming convention | Follows `[Project]-WF-[ScreenName]-v[X.X]` | "dashboard wireframe" (no standard naming) |
| LF-7 | Interaction states referenced | Wireframe notes which states apply ("See Phase 4 for Loading/Empty/Error/Success") | States not mentioned |

## Hi-Fi Prototype Acceptance Criteria

| **#** | **Criterion** | **Pass Condition** | **Fail Example** |
| --- | --- | --- | --- |
| HF-1 | All lo-fi criteria met | LF-1 through LF-7 pass | Missing layout grid or sample data |
| HF-2 | Design tokens applied | Colors, typography, spacing match token sheet exactly (hex values verifiable) | "Close enough" colors, wrong font |
| HF-3 | All 4 interaction states designed | Loading, Empty, Error, Success visually rendered for the screen | Only success state shown |
| HF-4 | Accessibility verified | Contrast ratios checked, ARIA roles annotated, keyboard flow documented | "We'll check a11y later" |
| HF-5 | Responsive variants | Desktop + tablet + mobile (if applicable) rendered as separate frames | Desktop only |
| HF-6 | Dev handoff annotations | Spacing values, component names, hover/focus/active states annotated | Flat screenshot with no annotations |
| HF-7 | Naming convention | Follows `[Project]-HF-[ScreenName]-v[X.X]` | Unnamed Figma frame |

## Ticket Integration

Every UI dev ticket **must** include:

1. **Wireframe link** — URL to the wireframe spec (blocks ticket from moving to "In Progress" without it)
2. **Interaction states reference** — which states apply to this screen
3. **A11y checklist items** — the specific accessibility requirements for this screen
4. **Token reference** — link to the design token sheet
5. **Acceptance criteria** — at minimum: "Screen matches wireframe layout. All 4 interaction states implemented. A11y checklist items pass."

<aside>
🚫

**Hard Rule:** No UI ticket moves to "In Progress" without a wireframe link and interaction states reference. The Steward PM enforces this at sprint planning.

</aside>

---

# 5 · Enforcement & Governance Rules

## Roles & Responsibilities

| **Role** | **Responsibility** | **Cadence** |
| --- | --- | --- |
| **Project PM** | Creates wireframes, specs interaction states, declares WCAG, defines tokens, submits weekly report, resolves blockers | Daily + Friday EOD |
| **Steward PM** | Reviews all 4 project submissions, enforces gates at Monday meeting, escalates overdue decisions, validates RAD log compliance | Monday meeting + Friday review |
| **Jorge (Reviewer)** | Signs off on gate transitions, resolves escalated decisions, approves hi-fi prototypes, conducts final compliance review | Gate reviews + Mar 20 final review |
| **CTO** | Receives escalations for blockers >5 days, approves exceptions to gates | As needed |

## Escalation Ladder

| **Trigger** | **Escalation Level** | **Action** | **SLA** |
| --- | --- | --- | --- |
| UI/UX decision unowned for >24hr | Steward PM | Assigns owner at next Monday meeting or ad-hoc | 24hr |
| Blocker unresolved for >3 days | Jorge | Shreyas/Vraj reviews and either resolves or assigns resource | 48hr |
| Gate failure for >1 sprint | Jorge | Project review meeting — assess if project scope needs adjustment | 5 business days |
| Friday report not submitted | Steward PM | PM named at Monday meeting. 2nd consecutive miss = CTO notification | Next Monday |
| Blocker unresolved for >5 days | Jorge | CTO intervenes directly — resource reallocation or scope decision | 48hr |

## Gate Exception Process

If a project cannot meet a gate criterion:

1. PM submits a written **Gate Exception Request** (1 paragraph: what's blocked, why, proposed resolution, timeline)
2. Jorge reviews within 24hr
3. If approved: exception is logged in RAD log with expiration date (max 1 sprint)
4. If denied: PM must remediate before next gate check
5. **No more than 1 active exception per project.** Second exception triggers CTO review.

---

# 6 · 7-Day Compliance Action Plan

<aside>
📅

**Goal:** All 4 projects pass Gate G2 (Interaction & A11y Ready) by March 20, 2026 for Jorge's review.

</aside>

## Day 1 — Monday Mar 17 (Today)

| **Action** | **Owner** | **Output** |
| --- | --- | --- |
| Finalize wireframe layout specs for Exec Dashboard + StakeAI (3 screens each) | Shreyas | 6 wireframe specs documented in project pages |
| Finalize wireframe layout specs for Woodside + RapdAI (3 screens each) | Vraj | 6 wireframe specs documented in project pages |
| Declare WCAG 2.1 AA for Exec Dashboard + StakeAI | Shreyas | Declaration + per-screen a11y checklists |
| Declare WCAG 2.1 AA for Woodside + RapdAI | Vraj | Declaration + per-screen a11y checklists |
| Fill design token hex values for Exec Dashboard | Shreyas | Token sheet with RAG colors, typography, spacing, backgrounds |
| Fill design token hex values for Woodside | Vraj | Token sheet with KIPS colors, traffic lights, brand palette |

## Day 2 — Tuesday Mar 18

| **Action** | **Owner** | **Output** |
| --- | --- | --- |
| Fill design token values for StakeAI | Shreyas | Token sheet with node types, edge weights, confidence tiers |
| Fill design token values for RapdAI | Vraj | Token sheet with status colors, chat tokens, file type accents |
| Spec interaction states for Exec Dashboard (Financial + Projects tabs) + StakeAI (all 3 screens) | Shreyas | 100% interaction state coverage for Exec Dashboard + StakeAI |
| Spec interaction states for Woodside (all 3 screens) + RapdAI (all 3 screens) | Vraj | 100% interaction state coverage for Woodside + RapdAI |
| Assign owners + due dates to Exec Dashboard + StakeAI open decisions | Shreyas | 8 decisions populated (M1-M3 + S1-S5) |
| Assign owners + due dates to Woodside open decisions | Vraj | 7 UI/UX + 10 client decisions populated (W1-W7) |

## Day 3 — Wednesday Mar 19

| **Action** | **Owner** | **Output** |
| --- | --- | --- |
| Lock Exec Dashboard decisions (M1, M2, M3) | Shreyas | 3 decisions moved from "Open" to "Locked" with rationale |
| Lock StakeAI decisions (S1-S5: confidence, graph library, MVP views, RBAC, performance) | Shreyas | 5 StakeAI decisions locked |
| Lock Woodside decisions (W1-W7) + follow up on client decisions | Vraj | 7 UI/UX decisions locked + client decision follow-up sent |
| Create visual wireframe export for Exec Dashboard Overview tab | Shreyas + Design | 1 visual wireframe in design tool |
| Create visual wireframe export for Woodside Dashboard | Vraj + Design | 1 visual wireframe in design tool |

## Day 4 — Thursday Mar 19

| **Action** | **Owner** | **Output** |
| --- | --- | --- |
| Submit EOD report for Exec Dashboard + StakeAI | Shreyas | 2 RAD log UI/UX sections submitted using template |
| Submit EOD report for Woodside + RapdAI | Vraj | 2 RAD log UI/UX sections submitted using template |
| Run Lighthouse audit on Exec Dashboard V1.0 | Shreyas | Lighthouse score recorded (target ≥ 90) |
| Validate wireframe specs for Exec Dashboard + StakeAI against LF-1 through LF-7 | Shreyas | 6 wireframes pass all 7 criteria or exceptions documented |
| Validate wireframe specs for Woodside + RapdAI against LF-1 through LF-7 | Vraj | 6 wireframes pass all 7 criteria or exceptions documented |
| Resolve remaining Woodside client decisions (10 pending) | Vraj + Client PM | Decisions logged with rationale or exception requested |

## Day 5 — Friday Mar 20 (Review Day)

| **Action** | **Owner** | **Output** |
| --- | --- | --- |
| Final RAD log review — cross-validate each other's 2 project submissions | Shreyas reviews Vraj's · Vraj reviews Shreyas's | Compliance confirmation or remediation list |
| Pre-stage Jorge review package — compile Exec Dashboard + StakeAI pages | Shreyas | Review-ready package for 2 projects |
| Pre-stage Jorge review package — compile Woodside + RapdAI pages | Vraj | Review-ready package for 2 projects |
| Final compliance review (present all 4 projects to Jorge for sign-off) | Shreyas + Vraj | Pass / Conditional Pass / Fail per project |
| Gate G2 status recorded for all 4 projects | Shreyas (Steward PM) | Gate status in RAD log — projects cleared for build phase |

---

# 7 · AI-Assisted Engineering — Industry Benchmark

<aside>
🤖

**Source:** [Uber CTO Praveen Neppalli Naga — Mar 17, 2026](https://x.com/praveenTweets/status/2033627282418655711) · Corroborated by The Hans India reporting.

</aside>

Uber's engineering org has undergone a fundamental shift that directly validates the governance model in this playbook. Their data proves that **the PM/engineering role is moving from code execution to oversight, validation, and system design** — exactly the pattern our gate system enforces for UI/UX.

## Key Data Points

| **Metric** | **Value** | **Relevance to Our Workflow** |
| --- | --- | --- |
| Code changes written entirely by AI agent | **1,800/week** | Our wireframe specs and interaction state docs are the "oversight layer" — without them, AI-generated UI code has no validation target |
| Engineers using AI tools monthly | **95%** | Assume our devs will use AI to generate UI components — token sheets and a11y checklists become the acceptance criteria AI output is measured against |
| Committed code that is machine-generated | **~70%** | If 70% of our UI code is AI-generated, wireframe specs (LF-1 through LF-7) are the only source of truth for what "correct" looks like |
| AI agent contribution growth | **<1% → 8% in months** | Rapid scaling means governance must be in place *before* AI output accelerates — retrofitting standards after the fact is 10× harder |
| Engineers using agent-style workflows | **84%** | Our PMs should expect devs to delegate entire screen builds to agents — the gate system ensures output quality regardless of who/what wrote the code |

## Industry Comparison

| **Company** | **AI-Generated Code %** | **Source** |
| --- | --- | --- |
| Uber | ~70% of committed code | CTO Praveen Neppalli Naga (Mar 2026) |
| Google | >30% of new code | CEO Sundar Pichai (2025) |
| Microsoft | 20-30% of repo code | CEO Satya Nadella (2025) |
| Anthropic | ~100% (AI-native) | Internal tooling reports |

## What This Means for aosenuma

<aside>
💡

**The Uber data validates our entire governance approach.** As AI agents write more code, the PM's role shifts from "make sure devs build it right" to "make sure the specs are right so AI builds it right." Our 8-phase compliance system, gate milestones, and acceptance criteria (LF-1 through LF-7, HF-1 through HF-7) are not bureaucracy — they are the **input layer** that AI agents will consume to generate correct UI.

</aside>

### Immediate Actions Based on This Data

1. **Treat wireframe specs as AI-consumable artifacts** — structured layout specs with px dimensions, sample data, and component inventories are exactly what coding agents need as input. Our LF-1 through LF-7 criteria already align with this.
2. **Design token sheets become machine-readable contracts** — hex values, spacing scales, and component names in our token sheets can be fed directly into AI coding agents. Ensure token naming follows CSS custom property conventions (`--color-*`, `--space-*`).
3. **Interaction state copy strings are AI prompt material** — the Loading/Empty/Error/Success copy we've defined for all 12 screens can be used as direct input for AI-generated UI components.
4. **Gate G4 (Ship Readiness) must include AI output validation** — if AI agents generate UI code, Lighthouse audits and a11y checklist verification become non-negotiable. The human role is to *validate*, not to *write*.
5. **Friday reports should track AI-assisted vs manual screens** — as we adopt AI coding tools, knowing which screens were AI-generated helps prioritize human review effort.

---

# 8 · Top 5 Risks & Mitigations

| **#** | **Risk** | **Likelihood** | **Impact** | **Mitigation** |
| --- | --- | --- | --- | --- |
| R1 | **PMs treat wireframe specs as optional** — submit text descriptions instead of structured layout specs with dimensions and sample data | High | High | Hard gate G1: wireframes must pass LF-1 through LF-7 acceptance criteria. Steward PM validates at Monday meeting. Non-compliant wireframes are rejected same-day. |
| R2 | **Decisions stay "Open" indefinitely** — no owner takes responsibility, decisions drift past deadline | High | High | Escalation ladder: unowned >24hr → Steward PM assigns. >3 days → Jorge. >5 days → CTO. Friday report makes open decisions visible weekly. |
| R3 | **Accessibility becomes checkbox theater** — WCAG declared but never tested, checklists created but never verified | Medium | High | Gate G4 requires Lighthouse ≥ 90 before ship. Per-screen a11y checklists are verified during QA, not just PM sign-off. Random spot-checks by Jorge. |
| R4 | **Friday reports become copy-paste with stale data** — PMs submit same numbers week over week | Medium | Medium | Steward PM cross-checks wireframe links in report against actual project repo. Any discrepancy flagged at Monday meeting. Require delta from previous week. |
| R5 | **Woodside client decisions block compliance** — 10 pending decisions depend on client response outside PM control | Medium | High | Gate Exception Process allows 1-sprint exception per project. PM documents "decision assumed as X" with client notification. If client overrides, rework is scoped as change request. |

### Failure Mode Prevention Checklist

<aside>
🛡️

**Common failure modes observed across all 4 projects and how to prevent them:**

</aside>

1. **"We'll add wireframes after build"** → **Prevention:** G1 gate blocks build. No wireframe = no sprint planning for UI tasks. Period.
2. **"Accessibility is a post-launch fix"** → **Prevention:** G2 requires WCAG declaration + a11y checklists before UI dev tickets are assigned. G4 requires Lighthouse ≥ 90 before deploy.
3. **"The design system is shadcn defaults"** → **Prevention:** Token sheet with project-specific hex values is a G2 requirement. Generic "shadcn" without values fails.
4. **"Interaction states are obvious"** → **Prevention:** 4 states (Loading/Empty/Error/Success) with real copy strings must be documented. "Will handle in code" is a gate failure.
5. **"One person can do all of this"** → **Prevention:** Steward PM rotation distributes enforcement. No single PM can self-approve their own gate passage — peer review is mandatory.

---

<aside>
🎯

**Success Criteria for March 20:** All 4 projects pass Gate G2. All Friday reports submitted. All decisions have owners. Zero overdue blockers. Jorge approves or conditionally approves each project for the next phase.

</aside>