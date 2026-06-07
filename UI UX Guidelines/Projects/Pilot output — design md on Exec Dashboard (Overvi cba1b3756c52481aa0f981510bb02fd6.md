# Pilot output — design.md on Exec Dashboard (Overview + KPI Card)

## Pilot objective

Prove `design.md` is usable as an end-to-end build spec for 1 screen + 1 component on an active project (Executive Dashboard).

## Pilot scope

- Screen: Exec Dashboard — Overview Tab (layout + interactions)
- Component: KPI Card (click → drill-down / slide-over)

## Inputs (from project compliance)

- Personas:
    - Executive (scan → identify risk)
    - Operator (drill → export → follow up)
- Navigation: Tabs (Overview / Commercial / Financial / Projects)
- Required states: Loading / Empty / Error / Success
- Accessibility target: WCAG 2.1 AA

---

## Prompt A result — New screen layout (Exec Dashboard: Overview Tab)

### 1) Component tree (ShadCN components + layout)

- Page Shell
    - Tabs (shadcn/ui: Tabs)
        - TabsList: Overview / Commercial / Financial / Projects
        - TabsContent: Overview
    - Header Row
        - H1 title (optional): "Executive Dashboard"
        - Date Presets (ButtonGroup)
            - Button (ghost/outline): 7d / 30d (default) / 90d / YTD
            - Optional: DateRangePicker (Popover + Calendar)
    - Freshness Bar (Card or Alert)
        - Badge/Indicator per source (AIVI / Sales / PMO)
        - Tooltip on status dot (Tooltip)
        - Right-side text: "Last synced: …"
    - KPI Strip (responsive grid)
        - Grid (Tailwind: grid, gap-4)
            - KPI Card × 6–9 (Card)
                - CardHeader: label (small text)
                - CardContent: value + delta + RAG/status badge
                - CardFooter (optional): secondary metadata (freshness)
    - Main Content (responsive)
        - Left column (Charts)
            - Card: Revenue Pipeline chart container
            - Card: Project Health RAG chart container
        - Right column (Attention Lists)
            - Card: At-Risk Projects list
            - Card: Invoice Exceptions list
            - Card: Stale Proposals list
            - Each list row is a Button / Link with focus styles
    - Drill-down Detail (Sheet used as slide-over)
        - Sheet (shadcn/ui: Sheet)
            - Trigger: KPI Card (click/Enter/Space)
            - Content: details panel (tables/metrics)
            - Close: X + Escape; focus returns to trigger

### 2) Interaction notes (validation, errors, empty state)

- Date presets:
    - Selecting a preset updates the dashboard query parameters and triggers a refresh.
    - Show a toast on success: "Date range updated to Last 90 Days." (5s auto-dismiss).
- KPI Card drill-down:
    - Click/Enter/Space opens a right-side Sheet.
    - Sheet uses focus trap; Escape closes and returns focus to the originating KPI Card.
- Freshness Bar behavior:
    - Source statuses: Live (green), Degraded (yellow), Offline (red).
    - Each dot must have a text-equivalent tooltip (and `aria-label`).
- Error handling:
    - If full data fetch fails: show a top-of-tab Alert with Retry.
    - If partial source fails: show per-source degraded/offline state in freshness bar + keep cached values where possible.
- Empty state:
    - When no results in range: show centered empty state in main content area with CTA "Reset to Last 30 Days".

### 3) Token usage notes (colors/typography)

- Typography
    - Heading / labels: Bricolage Grotesque via `font-heading`
    - Body: Inter via `font-sans`
    - KPI values / numeric: Barlow via `font-footer` (or a dedicated `font-data` alias)
- Colors
    - Background uses tokens (no hex directly in components)
    - Focus ring uses `--ring` / primary token
    - RAG colors must be paired with text labels (never color-only)
- Spacing
    - KPI grid gap: 16px (`gap-4`)
    - Main content gutter: 24px (`gap-6`)

### 4) Acceptance criteria checklist (screen)

- [ ]  ShadCN components used (Tabs, Card, Badge, Tooltip, Sheet, Toast)
- [ ]  Token-driven styling only (no hard-coded colors)
- [ ]  States implemented: Loading / Empty / Error / Success
- [ ]  Accessibility: keyboard navigable, visible focus, semantic headings, tablist ARIA, tooltips have text equivalents
- [ ]  Drill-down panel works: focus trap + Escape close + focus return

---

## Prompt B result — Component generation/modification (KPI Card)

### Component name

KpiCard

### Intended usage

Display a single KPI with label, value, delta, and optional status/freshness; supports drill-down.

### Props (implementation-facing)

- label: string
- value: string | number
- deltaLabel?: string (e.g., "+4.2%" or "-$120K")
- trend?: "up" | "down" | "flat"
- ragStatus?: "onTrack" | "atRisk" | "blocked" | "unknown"
- freshness?: "live" | "degraded" | "offline"
- onOpenDetails?: () => void (or use as Sheet trigger)
- loading?: boolean
- disabled?: boolean

### Variants

- size: default / compact
- emphasis: normal / critical (e.g., atRisk or blocked)
- trend: up/down/flat (controls icon + color)

### Required states

- Loading: skeleton that preserves card dimensions
- Empty: show "—" for value + helper text "No data"
- Error/degraded/offline: show inline badge + tooltip explaining staleness; maintain readability
- Success: used only for downstream actions (e.g., export) via toast (not on the card itself)

### Accessibility notes

- KPI Card is keyboard focusable (Button-like semantics)
- Enter/Space triggers drill-down
- Includes text label for RAG status (not color only)
- Focus ring uses token ring color

### Example usage (pseudo)

- KpiCard used as a SheetTrigger; the Sheet content provides the drill-down details.

---

## PR snippet (filled for this pilot)

**UI/UX Standard compliance (required)**

- `design.md` referenced: (paste link to `design.md` in repo)
- Tokens used (no one-off colors): Yes
- ShadCN-first (fork documented if needed): Yes
- States included: Loading / Empty / Error / Success
- Accessibility: keyboard + focus + semantic structure verified: Yes
- Exceptions filed (if any): None

## Pilot outputs

- Screen spec: Overview Tab (component tree + interactions + AC)
- Component spec: KPI Card (props/variants/states/a11y)

## Pilot pass/fail criteria

Pass if a builder can implement the Overview Tab + KPI Card using only this spec + `design.md`, and the PR snippet can be completed with no exceptions.