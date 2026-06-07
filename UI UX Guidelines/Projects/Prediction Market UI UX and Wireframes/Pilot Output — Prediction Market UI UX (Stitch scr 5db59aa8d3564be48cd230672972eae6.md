# Pilot Output — Prediction Market UI/UX (Stitch screens + core components)

## Pilot objective

Prove `design.md` can produce a builder-ready spec for the Prediction Market UI using the current canonical artifacts (Stitch prototype + wireframe coverage) on this page.

## Pilot scope

- Product area: Prediction Market Edge Tool UI
- Inputs: canonical Stitch prototype + latest uploaded screens + wireframe coverage notes
- Outputs:
    - Prompt A result: Screen layout spec (Markets list)
    - Prompt B result: Component spec (Market Row)
    - Acceptance criteria checklist + PR snippet (ready to paste)

---

## Source inputs (from this page)

- Canonical prototype (Stitch): [https://stitch.withgoogle.com/preview/9779729415150906015?node-id=56f42087f00f4ecb9bac636767e5847c](https://stitch.withgoogle.com/preview/9779729415150906015?node-id=56f42087f00f4ecb9bac636767e5847c)
- Covered screens: Home, Markets list, Market detail, Edge analysis, Position builder, Portfolio
- Stated baseline:
    - Visual system: dark-first, 8pt spacing, 12px radius
    - Navigation: top app bar + bottom nav (Home/Markets/Portfolio)
    - Shared components: market row, probability chip, edge badge, chart card, sticky CTA bar
    - Required states: loading skeletons, empty states w/ CTA, inline error + retry

---

## Prompt A result — New screen layout (Markets list)

### 1) Component tree (ShadCN components + layout)

- App Shell
    - Top App Bar
        - Logo
        - Search input (Input + icon)
        - Alerts (Button + Badge)
        - Profile menu (DropdownMenu)
    - Bottom Navigation
        - Nav items: Home / Markets / Portfolio (Tabs or custom bottom nav)
- Markets List Screen
    - Header row
        - Page title: "Markets"
        - Sort control (Select)
    - Filter chips (horizontal scroll)
        - Chip: Category
        - Chip: Volume
        - Chip: Timeframe
        - Chip: Edge
    - Markets list
        - List container (Card or plain section)
        - Market Row × N
            - Market name + subtitle
            - Probability chip
            - Edge badge
            - Mini chart / sparkline (optional)
            - Row click → Market detail
    - Pagination / infinite scroll

### 2) Interaction notes

- Search
    - Typing filters results; debounce 300–500ms.
    - Empty state when no matches: "No markets match your search" + CTA "Clear search".
- Filters
    - Chips act as toggles; selected chips visible.
    - Provide "Reset filters" action when ≥1 chip selected.
- Row interaction
    - Row is keyboard-focusable.
    - Enter/Space opens Market detail.
- Error handling
    - Inline error block above list: "Unable to load markets" + Retry.
    - Preserve last-known results if available.

### 3) Token usage notes

- Theme: dark-first (ensure token set includes dark surfaces + contrast-safe text)
- Spacing: 8pt scale
- Radius: 12px default card radius
- Avoid one-off hex values in components; map to tokens.

### 4) Acceptance criteria (screen)

- [ ]  Navigation present (top app bar + bottom nav)
- [ ]  Loading / Empty / Error / Success states defined
- [ ]  Filters + search usable on keyboard
- [ ]  Row click + keyboard open detail works
- [ ]  All colors/spacing/radius are token-driven

---

## Prompt B result — Component generation/modification (Market Row)

### Component name

MarketRow

### Intended usage

Primary list row component for Markets list; summarizes a market and surfaces probability + edge.

### Props

- marketTitle: string
- marketSubtitle?: string
- probability: number (0–1) or string display (e.g., "62%")
- edgeLabel?: string (e.g., "+3.2%")
- volumeLabel?: string
- trend?: "up" | "down" | "flat"
- onOpen?: () => void
- loading?: boolean
- disabled?: boolean

### Variants

- density: default / compact
- emphasis: normal / highlighted (e.g., top opportunities)

### Required states

- Loading: skeleton row (preserve height + alignment)
- Empty: handled by screen-level empty state (row not rendered)
- Error: show inline “stale data” badge if row is cached while refresh fails
- Success: selection/open action is acknowledged via navigation (no toast required)

### Accessibility notes

- Entire row acts like a button/link; must be focusable with visible focus ring
- Provide `aria-label` that includes market title + probability

---

## PR snippet (filled for this pilot)

**UI/UX Standard compliance (required)**

- `design.md` referenced: (repo link)
- Tokens used (no one-off colors): Yes
- ShadCN-first (fork documented if needed): Yes
- States included: Loading / Empty / Error / Success
- Accessibility: keyboard + focus + semantic structure verified: Yes
- Exceptions filed (if any): None

## Pilot pass/fail criteria

Pass if a builder can implement Markets list + MarketRow using only this pilot output + `design.md`, with no exceptions required.