# Predictive Tool UI/UX — Update for Jorge

## Context (from UI/UX Process Assignment)

- We currently don’t have a consistent UI/UX process; this work is to establish a lightweight, repeatable approach.
- Goal: move from “no prototype/wireframe” → “something reviewable” → “repeatable process + artifacts” that fit our build workflow.

## What I started (this week)

I began producing UI/UX screens for the Predictive Tool / Market Intelligence experience to create a presentable baseline for review.

## Current screens (v0 draft)

### 1) Market List / Market Terminal

- Left nav: Markets, Portfolio, Signals, Analytics, Settings.
- Main content: Market List with filters (Category, Status, Liquidity Range), sorting (Edge strength), and search.
- Right panel: Market Details with quick chart, Volume/OI, Recent Trades, and “Edge Insights”.

### 2) Market Detail / Edge Analysis

- Market header + status.
- “Mispricing detected” banner with a numeric opportunity indicator.
- YES/NO contract cards with price + short-term delta.
- Order book depth table (split view / cumulative).
- Right-side “Edge Analysis” panel: confidence score, key bullets, volatility mini-chart, and whale movements.

### 3) Opportunities Queue / Signals

- Signals queue with sorting tabs (Confidence/Recency/Signal type) and state filters (Active/Bookmarked/Dismissed).
- List items include: category, market title, signal type, confidence, detected time.
- Right panel: signal analysis with “alpha edge”, liquidity, internal score, and chart.

## What this enables (immediate value)

- A reviewable prototype baseline for Jorge + team feedback.
- A shared UI vocabulary (navigation, information hierarchy, panels, edge callouts).
- A starting point for a repeatable UI/UX process (screens → feedback → iteration → build-ready specs).

## How this maps to the meeting action items

- Establish a prototype/wireframe baseline for the Prediction Markets tool.
- Start exploring an “agentic design” direction by turning this into structured UI artifacts that can later be captured as a Design MD + design system guidance.

## Decisions needed from Jorge (fast feedback)

1. Which IA is preferred for v0: “Market Intelligence” vs “Edge Ledger” vs “Equity Terminal” framing?
2. Should the default workflow be market-first (Markets) or signal-first (Opportunities/Signals)?
3. What’s the must-have set for v0: Market list + detail + queue (current), or are there other priority screens?

## Next steps (48–72 hours)

- Consolidate naming + navigation into one canonical layout.
- Turn these screens into a clickable flow (low effort prototype) and annotate key states.
- Produce a v0 “Design MD” draft (tokens, typography, spacing, component inventory) to support the agentic design approach.

## Open questions / risks

- Without a defined design system + component library, UI consistency could drift across features.
- Need clarity on which data is real-time vs batch so the UI reflects correct “Last updated” + confidence semantics.

![Screenshot 2026-03-26 171352.png](Predictive%20Tool%20UI%20UX%20%E2%80%94%20Update%20for%20Jorge/Screenshot_2026-03-26_171352.png)

![Screenshot 2026-03-26 171401.png](Predictive%20Tool%20UI%20UX%20%E2%80%94%20Update%20for%20Jorge/Screenshot_2026-03-26_171401.png)

![Screenshot 2026-03-26 171409.png](Predictive%20Tool%20UI%20UX%20%E2%80%94%20Update%20for%20Jorge/Screenshot_2026-03-26_171409.png)