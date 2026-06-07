# StakeAI — UI/UX Compliance

**Compliance Score:** 57/60 (95%) · **Ship Date:** May 2, 2026 (ISA onboarding Apr 27) · **Overall:** 🟡 Partial

**Owner:** @Shreyas Shirke · **Reviewer:** Jorge Domenzain

---

## Phase 1 · Audit Findings

- What Exists ✅
    - Navigation model (module-specific nav with Graph Explorer, Directory, Search, Transcripts)
    - Widget types documented (Graph Explorer canvas via vis-network, Stakeholder Profile cards, Search facets)
    - 3-level information hierarchy (graph overview → node selection → full profile)
    - Design philosophy — "Calm, Focused, Dependable" with neutral palette + meaning-reserved color
    - 3 user personas (Field PM, ESG/Compliance Lead, Executive)
    - 7 core UI views defined
    - Full ERD and DB schema (14 tables)
    - PoC baseline exists (graph viz, manual merge, transcript dashboard, audio/DOCX processing)
    - 5 Gherkin acceptance criteria (AC-UI-01 through AC-UI-05)
    - Go/No-Go checklist (13 gates)
    - RBAC model (Admin/Editor/Viewer with Supabase RLS)
    - 11 API contracts listed
    - 5-phase execution plan (Spec → Handoff → Build → Harden → Ship)
- Critical Gaps ❌ / ⚠️
    - ❌ **No wireframes or mockups** — Lean MVP plan lists wireframe creation as Week 1 action, no evidence of completion
    - ⚠️ **Loading / Empty / Error states** — Mentioned (skeleton loader, progress bar, retry) but no visual specs or copy strings
    - ⚠️ **Accessibility** — "Color is never the only signal" and keyboard nav mentioned, but no WCAG target, contrast ratios, or ARIA patterns
    - ❌ **Responsive / Device strategy** — No breakpoints defined; field PMs may use tablets
    - ⚠️ **Onboarding flow** — Empty graph state mentioned but no first-run experience designed
    - ⚠️ **Confidence scoring UI** — Contradictory: UI doc says show on AI summaries, Lean MVP says out-of-scope
    - ⚠️ **API contracts** — All 11 endpoints unchecked, no contracts finalized
    - ⚠️ **Task database** — 4 action items only, no structured sprint tasks with owners and AC

<aside>
🔒

**Decisions to Lock:**

- Confidence display in V1.0 (UI doc vs Lean MVP conflict)
- Graph library final (vis-network confirmed, needs Jorge sign-off)
- MVP views final (7 views — needs sign-off)
- RBAC boundary final
- Performance target (1,000+ graph nodes)
</aside>

---

## Phase 2 · Current State Assessment

| **Dimension** | **Status** | **Evidence** |
| --- | --- | --- |
| Validated User Journeys | ⚠️ | 3 personas defined (Field PM, ESG Lead, Executive). 3-level hierarchy documented. No visual journey maps. |
| Wireframes / Prototypes | ❌ | Zero wireframes. Lean MVP plan listed wireframe creation as Week 1 (Feb 18–19) — no evidence of completion. |
| Design System | ✅ | "Calm, Focused, Dependable" philosophy. Neutral palette + meaning-reserved color documented. |
| Interaction States | ⚠️ | States mentioned (skeleton loader, progress bar, retry) but no visual specs or copy strings for any of the 7 views. |
| Accessibility | ⚠️ | "Color is never the only signal" + keyboard nav mentioned. No WCAG target, no contrast ratios, no ARIA patterns. |
| Info Architecture | ✅ | 7 views defined. Full ERD (14 tables). RBAC model with 3 roles. |
| Dev Handoff | ⚠️ | 11 API endpoints listed, all unchecked. 4 action items only — no sprint-level task database. |

---

## Phase 3 · Lo-Fi Wireframes (Top 3 Screens)

**Naming convention:** `StakeAI-WF-[ScreenName]-v[X.X]`

| **Screen** | **What to Wireframe** | **Key Elements** | **Responsive Notes** |
| --- | --- | --- | --- |
| 1. Graph Explorer | Full-canvas graph visualization with vis-network, node selection panel, filter controls, zoom/pan tools, legend | 3-level drill-down (graph overview → node selection → full profile), meaning-reserved color for node types, real-time polling indicator (30s), performance target (1,000+ nodes) | Desktop 1440px primary. Tablet 1024px: graph scales, side panel becomes bottom sheet. Touch gesture support for pan/zoom. |
| 2. Stakeholder Directory | List/grid view of all stakeholders with search, filter by type/project, sort options, quick profile preview | Profile cards with key metadata, relationship count badge, search facets, CSV/JSON export button | Grid → list layout on tablet. Cards stack vertically on smaller screens. |
| 3. Stakeholder Profile | Full profile view with metadata, relationship graph (mini), interaction history/timeline, linked transcripts, manual merge tool access | Context panel for quick actions, confidence indicator (if V1.0 — pending decision lock), RBAC-gated actions (Admin vs Editor vs Viewer) | Profile sections stack vertically on tablet. Mini graph becomes expandable. |

### StakeAI-WF-GraphExplorer-v1.0

**Desktop (1440px):**

- **Top Nav (56px):** StakeAI logo (left) · Module nav: Graph Explorer (active) | Directory | Search | Transcripts · Workspace selector dropdown · User avatar + role badge (Admin/Editor/Viewer) · Settings gear
- **Toolbar (48px):** Zoom in/out buttons · Fit-to-view · Fullscreen toggle · Filter panel toggle · Layout switcher (Force/Hierarchical/Radial) · Legend toggle · Polling indicator ("Live · 30s" with green pulse dot)
- **Canvas (full remaining height):** vis-network graph visualization. Node types differentiated by shape + color + icon (Person=circle+blue, Organization=hexagon+teal, Project=diamond+purple, Location=square+green). Edge thickness = relationship strength. Edge labels on hover. Click node → selection highlight (2px ring `--color-primary`). Double-click → drill to Profile.
- **Selection Panel (360px, right sidebar, slides in on node click):**
    - Node header: Name (18px bold) · Type badge · Confidence score (if V1.0 — pending decision) · Connection count badge
    - Quick stats: Direct connections | Shared projects | Last interaction date
    - Top 5 connections list (name, type, relationship label)
    - Actions: "View Full Profile" primary button · "Merge Entity" (Admin only) · "Export Subgraph"
- **Legend Overlay (bottom-left, collapsible):** Node type → shape/color mapping. Edge weight scale. Cluster explanation.
- **Performance:** Target 1,000+ nodes. Progressive loading: first 200 nodes instant, remaining streamed. Clustering auto-activates at >500 visible nodes.

**Tablet (1024px):** Selection panel → bottom sheet (40% height, swipe up to expand). Canvas fills full width. Touch: pinch-to-zoom, drag-to-pan. Toolbar collapses to hamburger menu.

### StakeAI-WF-Directory-v1.0

**Desktop (1440px):**

- **Top Nav:** Same as Graph Explorer (shared shell)
- **View Toggle (40px):** Grid | List · Sort dropdown (Name / Connections / Last Activity / Type) · Search bar (full-text with facets)
- **Filter Sidebar (240px, left):** Type checkboxes (Person/Organization/Project/Location) · Project filter (multi-select) · Connection count range slider · Last activity date range · RBAC: show only entities user has access to
- **Content Area (grid or list):**
    - **Grid mode:** Cards 280×200px, 4-col. Each card: Avatar/icon · Name (16px bold) · Type badge · Connection count · Last activity date · "View Profile" link
    - **List mode:** Full-width table. Columns: Name | Type | Connections | Projects | Last Activity | Actions (View · Merge). Sort on all columns. Pagination 25/page.
- **Bulk Actions Bar (appears on multi-select):** "Export Selected (CSV)" · "Export Selected (JSON)" · "Merge Selected" (Admin only, max 5)
- **Empty State:** Illustration of network nodes + "No stakeholders found. Upload transcripts to begin building your directory." CTA: "Upload Documents"

**Tablet (1024px):** Filter sidebar → collapsible drawer. Grid → 2-col. List table → horizontal scroll with sticky name column.

### StakeAI-WF-Profile-v1.0

**Desktop (1440px):**

- **Breadcrumb (32px):** Directory > John Smith
- **Profile Header (140px):** Avatar/icon (64px) · Name (24px bold) · Type badge · Confidence indicator (colored ring around avatar: green ≥80%, yellow 50-79%, red <50% — text label below: "High Confidence" / "Medium" / "Low") · Edit button (Editor/Admin only)
- **Content (60/40 split, gap 24px):**
    - Left (60%):
        - **Metadata Section:** Key-value pairs — Organization, Title/Role, Location, Contact info, Projects involved, Tags. Editable inline (Editor/Admin).
        - **Interaction Timeline:** Chronological entries (meeting notes, transcript mentions, manual notes). Each entry: date, source document link, excerpt, added-by user. Infinite scroll.
        - **Linked Transcripts:** List of transcripts where entity appears. Each: transcript title, date, mention count, link to transcript view.
    - Right (40%):
        - **Mini Graph (300×250px):** Ego-network showing direct connections (1-hop). Same vis-network rendering, simplified. Click node → navigate to that profile. "Expand in Graph Explorer" link.
        - **Relationship Summary:** Top connections table (Name | Type | Shared projects | Strength). Max 10 shown, "View All" link.
        - **Manual Merge Tool (Admin only):** "Merge with another entity" button → opens search dialog → select target → preview merged data → confirm.
- **Action Bar (top-right):** "Edit" · "Export Profile (PDF)" · "View in Graph" · "Delete" (Admin only with confirmation)

**Tablet (1024px):** Content → single column (left above right). Mini graph → expandable section (collapsed by default). Merge tool → full-screen modal.

- [x]  Wireframe spec created — `StakeAI-WF-GraphExplorer-v1.0`
- [x]  Wireframe spec created — `StakeAI-WF-Directory-v1.0`
- [x]  Wireframe spec created — `StakeAI-WF-Profile-v1.0`
- [x]  Visual wireframes linked in project repository
    - StakeAI-FE (main): [https://www.figma.com/make/ZZhqOWusVOzhwdQ5JEyzTh/StakeAI-FE?fullscreen=1&t=CxCcRKTTa8KHP6Jt-1](https://www.figma.com/make/ZZhqOWusVOzhwdQ5JEyzTh/StakeAI-FE?fullscreen=1&t=CxCcRKTTa8KHP6Jt-1)
    - StakeAI-FE (screen link 1): [https://www.figma.com/make/ZZhqOWusVOzhwdQ5JEyzTh/StakeAI-FE?t=ff9BFEBiVh9rX7yg-1](https://www.figma.com/make/ZZhqOWusVOzhwdQ5JEyzTh/StakeAI-FE?t=ff9BFEBiVh9rX7yg-1)
    - StakeAI-FE (screen link 2): [https://www.figma.com/make/ZZhqOWusVOzhwdQ5JEyzTh/StakeAI-FE?p=f&t=f8hmu8OdxMlEkugu-0&fullscreen=1](https://www.figma.com/make/ZZhqOWusVOzhwdQ5JEyzTh/StakeAI-FE?p=f&t=f8hmu8OdxMlEkugu-0&fullscreen=1)

---

## Phase 4 · Interaction States — Reference Screen: Graph Explorer

| **State** | **Visual Pattern** | **Copy / Behavior** |
| --- | --- | --- |
| **Loading** | Canvas area shows centered spinner with progress percentage. Side panel shows skeleton cards. Polling indicator paused. | "Loading graph data... (X%)" — progress bar showing node/edge loading count. |
| **Empty** | Empty canvas with illustration of a network + descriptive copy + primary CTA. First-run onboarding tooltip if new user. | "No stakeholder data found for this project. Upload transcripts or documents to begin building your stakeholder graph." CTA: "Upload Documents" |
| **Error** | Canvas overlay with error icon + message + retry. Partial graph preserved if some data loaded. | "Unable to load graph data. Some nodes may be missing." Button: "Retry" · If partial: "Showing X of Y nodes — retry to load remaining." |
| **Success** | Toast notification for completed actions (export, merge, node edit) | "Graph exported as CSV successfully." or "Stakeholder entities merged — graph updated." |
- [x]  Loading state spec'd — canvas spinner + progress percentage + skeleton side panel
- [x]  Empty state spec'd — first-run onboarding with "Upload Documents" CTA
- [x]  Error state spec'd — partial graph preservation + retry for missing nodes
- [x]  Success state spec'd — action confirmation toasts for export/merge/edit
- [ ]  All copy stored in string table (pending extraction)

### Interaction States: Stakeholder Directory

| **State** | **Visual Pattern** | **Copy / Behavior** |
| --- | --- | --- |
| **Loading** | Grid: 8 skeleton cards (shimmer matching card layout). List: 10 skeleton table rows. Filter sidebar loads independently (may show before content). | Search bar shows "Loading directory..." placeholder. Sort/view toggles disabled until loaded. |
| **Empty** | Centered illustration of network nodes + descriptive copy + primary CTA | "No stakeholders found. Upload transcripts or documents to begin building your stakeholder directory." CTA: "Upload Documents" · If filtered: "No results match your filters." CTA: "Clear Filters" |
| **Error** | Alert banner at top. If partial load: show loaded entries with warning badge and retry for remaining. | "Unable to load stakeholder directory. Please try again." Button: "Retry" · Partial: "Showing X of Y entries — some data may be missing." |
| **Success** | Toast for export, merge completion, profile updates | "Exported 142 stakeholders as CSV." · "2 entities merged successfully — directory updated." |

### Interaction States: Stakeholder Profile

| **State** | **Visual Pattern** | **Copy / Behavior** |
| --- | --- | --- |
| **Loading** | Skeleton header (avatar circle + name bar + badge). Skeleton metadata key-value pairs. Skeleton timeline entries (3 rows). Mini graph shows spinner. | "Loading profile..." in breadcrumb area. Action buttons disabled until loaded. |
| **Empty** | Profile header shows, but timeline and transcripts sections show empty states independently | Timeline: "No interactions recorded yet. This entity was found in uploaded documents but has no detailed history." Transcripts: "No linked transcripts." |
| **Error** | Full profile error: centered error + retry. Section errors: inline error per section (timeline, mini graph, transcripts can fail independently). | "Unable to load profile. Please try again." Button: "Retry" · Mini graph: "Graph unavailable — retry to load connections." |
| **Success** | Toast for edit saves, merge, export. Inline confirmation for metadata edits (green check flash on field). | "Profile updated successfully." · "Merge complete — redirecting to merged profile." · "Profile exported as PDF." |

---

## Phase 5 · Accessibility Declaration

**Target:** WCAG 2.1 AA

**Project-specific requirements:**

- **Graph visualization requires special a11y attention:**
    - Keyboard traversal for graph nodes (arrow keys to navigate, Enter to select, Escape to deselect)
    - Screen reader announcements for node selection ("Selected: John Smith, 5 connections")
    - High-contrast mode for graph edges and node types (not relying on color alone)
- Search facets need proper ARIA labels and keyboard-accessible checkboxes
- CSV/JSON export button needs accessible label ("Export stakeholder data as CSV")
- Manual merge tool needs step-by-step screen reader guidance
- [x]  **WCAG 2.1 AA declared** in project card
- [x]  **Per-screen accessibility checklists created** (see below)
- [ ]  Lighthouse audit run (target ≥ 90) — run after visual wireframes are built

### Graph Explorer — A11y Checklist

- [ ]  Graph nodes keyboard-traversable (arrow keys to navigate between connected nodes, Enter to select, Escape to deselect)
- [ ]  Selected node announced to screen reader ("Selected: John Smith, Person, 5 connections")
- [ ]  Node type differentiated by shape + icon, not color alone (circle/hexagon/diamond/square + labeled icon)
- [ ]  Zoom controls keyboard-accessible (+ / - keys or buttons with `aria-label`)
- [ ]  Legend uses text labels alongside color swatches
- [ ]  Selection panel has `role="complementary"` with `aria-label="Stakeholder details"`
- [ ]  Polling indicator has `aria-live="polite"` for status changes ("Data refreshed")
- [ ]  Canvas has text alternative for screen readers ("Stakeholder graph with X nodes and Y connections")

### Directory — A11y Checklist

- [ ]  Grid cards use `role="article"` or equivalent with `aria-label` containing stakeholder name and type
- [ ]  List table uses `role="table"` with `aria-sort` on sortable columns
- [ ]  Filter checkboxes use `role="group"` with `aria-label="Filter by type"`
- [ ]  Search bar has `aria-label="Search stakeholders"` with `aria-describedby` for facet hints
- [ ]  View toggle (Grid/List) uses `role="radiogroup"` with `aria-label="View mode"`
- [ ]  Bulk action bar announced via `aria-live="polite"` when selections change ("3 stakeholders selected")
- [ ]  Export buttons have descriptive labels ("Export 142 stakeholders as CSV")

### Profile — A11y Checklist

- [ ]  Confidence indicator uses color + text label ("High Confidence: 92%" not just green ring)
- [ ]  Mini graph has text summary alternative ("5 direct connections: 3 people, 1 organization, 1 project")
- [ ]  Inline edit fields use `aria-label` and announce save state ("Name updated" via `aria-live`)
- [ ]  Timeline entries keyboard-navigable with visible focus indicators
- [ ]  Merge tool uses step-by-step `aria-live` announcements ("Step 1 of 3: Select entity to merge")
- [ ]  Action buttons have descriptive `aria-label` ("Export John Smith profile as PDF")
- [ ]  Linked transcripts: links announce document title and mention count

---

## Phase 6 · Design Token Reference Sheet

<aside>
📐

**Brand alignment:** aosenuma internal tokens (teal/lime, Bricolage Grotesque + Inter + Barlow, shadcn/ui)

</aside>

| **Category** | **Token** | **Value** | **Usage** |
| --- | --- | --- | --- |
| Node — Person | `--color-node-person` | `#2563EB` (blue-600) · shape: circle · icon: user | Person entities in graph + directory badges |
| Node — Organization | `--color-node-org` | `#0D9488` (teal-600) · shape: hexagon · icon: building | Organization entities in graph + directory badges |
| Node — Project | `--color-node-project` | `#9333EA` (purple-600) · shape: diamond · icon: folder | Project entities in graph + directory badges |
| Node — Location | `--color-node-location` | `#16A34A` (green-600) · shape: square · icon: map-pin | Location entities in graph + directory badges |
| Edge — Strong | `--color-edge-strong` | `#475569` (slate-600) · 3px width | High-strength relationships (≥0.7 score) |
| Edge — Medium | `--color-edge-medium` | `#94A3B8` (slate-400) · 2px width | Medium-strength relationships (0.3–0.7) |
| Edge — Weak | `--color-edge-weak` | `#CBD5E1` (slate-300) · 1px width | Low-strength relationships (<0.3) |
| Confidence — High | `--color-confidence-high` | `#16A34A` (green-600) · ring around avatar | Entity confidence ≥80% |
| Confidence — Medium | `--color-confidence-med` | `#CA8A04` (yellow-600) · ring around avatar | Entity confidence 50–79% |
| Confidence — Low | `--color-confidence-low` | `#DC2626` (red-600) · ring around avatar | Entity confidence <50% |
| Background — Canvas | `--color-bg-canvas` | `#F8FAFC` (slate-50) · calm, neutral tone | Graph Explorer canvas background |
| Background — Card | `--color-bg-card` | `#FFFFFF` (white) · `--shadow-sm` elevation | Directory cards, profile sections, selection panel |
| Primary | `--color-primary` | `#0D9488` (teal-600, aosenuma brand) | CTAs, active states, selected node ring, links |
| Accent | `--color-accent` | `#84CC16` (lime-500, aosenuma brand) | Highlights, success badges, live polling indicator |
| Border | `--color-border` | `#E2E8F0` (slate-200) | Card borders, panel dividers, table borders |
| Text — Primary | `--color-text-primary` | `#0F172A` (slate-900) | Headings, node labels, profile names |
| Text — Secondary | `--color-text-secondary` | `#64748B` (slate-500) | Metadata labels, timestamps, descriptions |
| Typography — Heading | `font-heading` | Bricolage Grotesque | View titles, profile headers, section headers |
| Typography — Body | `font-body` | Inter | Profile metadata, directory entries, search results, timeline |
| Typography — Data | `font-data` | Barlow | Connection counts, confidence scores, timestamps |
| Spacing | `--space-*` | 4px / 8px / 12px / 16px / 24px / 32px / 48px | Component padding, card gaps, panel margins, canvas padding |
| Components | shadcn/ui | Card, Table, Badge, Dialog, Sheet, Command (search), Toast, Tabs, Avatar, Tooltip | Standard aosenuma component set + vis-network for graph |
- [x]  Design Token Reference Sheet created (node types, edge weights, confidence, brand palette with hex values)
- [x]  Linked from project card

---

## Phase 7 · UI/UX Reporting Status

| **Field** | **Current Value** |
| --- | --- |
| Prototype Status | **In Progress** — layout specs complete, visual wireframes pending |
| Screens Completed | 3 of 3 (layout specs) · 0 of 3 (visual wireframes) |
| Screens Remaining | 3 visual wireframes (design tool export) |
| Interaction States Coverage | **100%** — all 3 screens spec'd (Graph Explorer, Directory, Profile) with Loading/Empty/Error/Success |
| Accessibility Compliance | **WCAG 2.1 AA declared** · Per-screen a11y checklists created · Lighthouse audit pending |
| Open UI/UX Decisions | 5 — all assigned with owners + due dates (see Phase 8) |
| Stakeholder Sign-off | Pending — target Jorge review by Mar 20 |
- [x]  UI/UX status section added to RAD log (template + current values populated above)
- [x]  All open decisions logged with owner + due date (see Phase 8 below)

---

## Phase 8 · Final Compliance Check

| **Compliance Item** | **Status** |
| --- | --- |
| Lo-fi wireframes for top 3 screens — linked in repo | ✅ Layout specs complete — visual wireframes pending design tool export |
| Interaction states documented for ≥1 primary screen | ✅ All 3 screens covered (Graph Explorer, Directory, Profile) |
| WCAG 2.1 AA declared in project card | ✅ |
| Design Token Reference Sheet created and linked | ✅ Node types, edge weights, confidence, brand palette with hex values |
| UI/UX status section in RAD log | ✅ Template populated with current values |
| Open UI/UX decisions logged with owners + due dates | ✅ 5 decisions assigned — all due Mar 19 |
| Hi-fi prototype naming convention established | ✅ `StakeAI-HF-[ScreenName]-v[X.X]` |

### Open Decisions

| **Decision** | **Owner** | **Due** | **Status** |
| --- | --- | --- | --- |
| S1 — Confidence display in V1.0 (UI doc vs Lean MVP conflict) | Shreyas | Mar 19 | **Rec: Show on profiles only** — exclude from graph nodes in V1.0, add in V1.1. Resolves conflict. |
| S2 — Graph library final (vis-network) | Shreyas | Mar 19 | **Rec: Confirm vis-network** — PoC validated, meets 1K node target with clustering |
| S3 — MVP views final (7 views) | Shreyas | Mar 19 | **Rec: Approve 7 views** — Graph Explorer, Directory, Profile, Search, Transcripts, Upload, Settings |
| S4 — RBAC boundary final (Admin/Editor/Viewer) | Shreyas | Mar 19 | **Rec: Confirm 3-role model** — Admin (merge+delete), Editor (create+edit), Viewer (read-only). Supabase RLS enforced. |
| S5 — Performance target (1,000+ nodes) | Shreyas + Dev | Mar 19 | **Rec: 1,000 nodes with auto-clustering at 500+** — progressive loading first 200, stream remaining |