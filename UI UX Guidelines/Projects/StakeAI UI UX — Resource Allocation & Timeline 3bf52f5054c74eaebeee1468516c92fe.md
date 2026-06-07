# StakeAI UI/UX — Resource Allocation & Timeline

**Prepared for:** Shreyas Shirke

**Date:** February 11, 2026

**Source:** Consolidated Planning Documents

---

# StakeAI UI/UX Resource Allocation

## UI/UX Team

| **Role** | **Person** | **Allocation** | **Timeline** | **Key Responsibilities** |
| --- | --- | --- | --- | --- |
| UI/UX Lead | **Shreyas Shirke** | Part-time (co-assigned with Dashboard UI/UX) | Feb 9 – Feb 28 | Navigation model, information hierarchy, design system, graph visualization UX |
| UI/UX Designer | **Vraj Patel** | Part-time (co-assigned with Dashboard UI/UX) | Feb 9 – Feb 28 | User flows, stakeholder profile views, search interface, accessibility |

## Development Team (Implementation)

| **Role** | **Person** | **Phase** | **Timeline** | **UI/UX Implementation Focus** |
| --- | --- | --- | --- | --- |
| Dev Lead | **Israel Ayala** | Phase 0: Oversight
Phase 1-2: Full-time | Feb 3 – May 2 | Technical architecture review, frontend framework decisions |
| Frontend Dev | **Vaishnavi Tapkire** | Phase 0 | Feb 3 – Mar 6 (departing) | Dashboard components, graph visualization implementation (Visx/vis-network) |
| Frontend Dev | **Koundinya Seshabhattar** | Phase 0-2 | Feb 3 – May 2 | Absorbs Vaishnavi's UI work, stakeholder profiles, search interface |
| Dev Support | **Kundana Pooskur** | Phase 1-2 | Mar 3 – May 2 | Tech review, UI component optimization |
| **Dev 4 (NEW)** | **Rishi Raj Kuleri** | Phase 0-2 | Feb 11 – May 2 | Frontend support, responsive design implementation |

---

# StakeAI UI/UX Master Timeline

## Design Phase (Feb 9 – Feb 28)

| **Week** | **Dates** | **UI/UX Deliverables** | **Owner** | **Status** |
| --- | --- | --- | --- | --- |
| Week 1 | Feb 9 – Feb 14 |   • Navigation model definition
  • Widget type specifications
  • Graph visualization UX design
  • Information hierarchy framework | Shreyas + Vraj | In Progress |
| Week 2 | Feb 17 – Feb 21 |   • Stakeholder profile view design
  • Search & discovery flow
  • Design system documentation
  • Real-time behavior specifications | Shreyas + Vraj | Planned |
| Week 3 | Feb 24 – Feb 28 |   • Design handoff documentation
  • Component specifications for dev team
  • Accessibility guidelines
  • Responsive design patterns | Shreyas + Vraj | Planned |

## Implementation Phase (Feb 3 – May 2)

| **Phase** | **Dates** | **UI/UX Implementation Milestones** | **Lead** | **Status** |
| --- | --- | --- | --- | --- |
| **Phase 0: Foundation** | Feb 3 – Mar 6 |   • Basic upload interface
  • Document processing status UI
  • Initial graph canvas setup (vis-network)
  • Transcript dashboard structure | Vaishnavi + Koundinya | 30% Complete |
| **Phase 1: MVP** | Mar 9 – Apr 18 |   • **Graph Explorer:** Interactive canvas with zoom/pan, filters, node selection
  • **Stakeholder Directory:** List/table view with search
  • **Profile Views:** Slide-over panel + full profile page
  • **Search Interface:** Global search with facet sidebar
  • **Transcripts View:** Source document repository UI | Israel + Koundinya + Rishi | Planned |
| **Phase 2: Polish** | Apr 20 – May 2 |   • UI performance optimization
  • Accessibility enhancements
  • Responsive design refinement
  • Empty states & loading states
  • User onboarding flows | Full Team | Planned |

---

# UI/UX Components Breakdown

## Module-Specific Components

| **Module** | **Components** | **Design Owner** | **Dev Owner** | **Target Date** |
| --- | --- | --- | --- | --- |
| 🕸️ **Graph Explorer** |   • Interactive vis-network canvas
  • Control bar (filters, layout toggle)
  • Context panel (slide-over)
  • Quick stats widget
  • Node/edge styling | Shreyas + Vraj | Koundinya + Rishi | Apr 18 |
| 👤 **Stakeholder Directory** |   • List/table view
  • Entity cards
  • Type badges
  • Sort/filter controls
  • Bulk actions | Shreyas + Vraj | Koundinya | Apr 18 |
| 🔍 **Search & Discovery** |   • Global search bar
  • Autocomplete
  • Facet sidebar
  • Results grid
  • Entity/transcript tabs | Shreyas + Vraj | Koundinya + Rishi | Apr 18 |
| 📄 **Transcripts** |   • Document repository
  • Upload interface
  • Processing status
  • Document cards
  • Preview modal | Shreyas + Vraj | Koundinya | Mar 28 |
| 📊 **Profile Views** |   • Header card
  • Summary widget (AI-generated)
  • Network card
  • Interaction timeline
  • Confidence indicators | Shreyas + Vraj | Koundinya + Rishi | Apr 18 |

---

# Design System Elements

## Color Palette (from UI/UX Documentation)

| **Element** | **Color** | **Usage** |
| --- | --- | --- |
| Base palette | White (#FFFFFF)
Light Gray (#F5F5F5)
Charcoal (#333333) | Calm, professional background |
| Entity: Person | Blue (#4A90D9) | Person nodes and badges |
| Entity: Organization | Gray (#8E8E93) | Organization nodes and badges |
| Sentiment: Positive | Green (#34C759) | Positive relationships |
| Sentiment: Risk | Red (#FF3B30) | At-risk relationships |
| Sentiment: Watch | Amber (#FF9500) | Relationships to monitor |

---

# Key Milestones & Dependencies

| **Milestone** | **Date** | **Description** | **Dependencies** |
| --- | --- | --- | --- |
| UI/UX Design Complete | Feb 28 | All design specs, component documentation, and design system delivered to dev team | None |
| Vaishnavi KT Complete | Feb 28 | Frontend architecture and component knowledge transferred to Koundinya + Rishi | UI/UX design specs available |
| Phase 0 UI Complete | Mar 6 | Basic interfaces for upload, processing, and transcript viewing | Vaishnavi departure, backend Phase 0 APIs |
| Graph Explorer MVP | Apr 18 | Interactive graph visualization with basic controls and context panel | Phase 1 backend (entity/relationship APIs) |
| Full UI/UX MVP | Apr 18 | All 4 modules functional with navigation, search, and profiles | Phase 1 complete |
| UI Polish & Production | May 2 | Performance optimized, accessible, responsive, production-ready | Phase 2 testing complete |

---

# Risks & Mitigation

| **Risk** | **Impact on UI/UX** | **Probability** | **Mitigation** |
| --- | --- | --- | --- |
| Vaishnavi departure (Mar 6) | High — Loss of frontend architecture knowledge and graph viz implementation experience | Certain |   • KT sessions daily Feb 11-14
  • Pair programming Feb 17-21
  • Shadow handoff Feb 24-28
  • Rishi added to absorb workload |
| Graph scaling (>10K nodes) | High — Performance degradation affects UX responsiveness | Medium |   • Optimize pgvector queries
  • Implement pagination/lazy loading
  • Design abstraction layer for future migration |
| Design-dev handoff gaps | Medium — Implementation may not match design intent | Medium |   • Component-level specifications
  • Design system documentation
  • Weekly design reviews with Israel |
| Responsive design complexity | Medium — Limited field connectivity requires mobile optimization | Low |   • Mobile-first approach for key flows
  • Progressive enhancement for desktop
  • Test on field devices |

---

**Sources:**

- [StakeAI UI/UX Documentation — V1.0](https://www.notion.so/StakeAI-UI-UX-Documentation-V1-0-dacd8d5aa57d4f1f9e18a3ba16e0c061?pvs=21)
- [2026 Priority Tracks — Consolidated Scope & Development Plan](https://www.notion.so/2026-Priority-Tracks-Consolidated-Scope-Development-Plan-3024544eeb42801eb9acc61659732102?pvs=21)
- [Consolidated Planning Document: RapdAI & StakeAI](https://www.notion.so/Consolidated-Planning-Document-RapdAI-StakeAI-3024544eeb4280349339cbe6cebac130?pvs=21)
- [PM SPRINT BRIEFING](https://www.notion.so/PM-SPRINT-BRIEFING-3024544eeb42800b95ded32f36c0ab9e?pvs=21)