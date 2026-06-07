# Stitch Prototype - using UI/UX guidelines - Shrey & Vraj

[Stitch - Design with AI](https://stitch.withgoogle.com/preview/13351878171131289754?node-id=13b5580c80f34bcabdfe3e8c8ec31a95)

<aside>
🦆

**Project roadmap — How Stitch generated this prototype & the workflow to ship it**
Owner: Shreyas & Vraj · Scope: understand Stitch pipeline, lock down export path, plug into aosenuma UI/UX standards.

</aside>

## Milestone 1 — How this prototype was generated (under the hood)

When the Stitch project was created, this pipeline ran end-to-end:

1. **Prompt intake** — natural-language brief (app type, target user, key screens, style) is sent to Gemini.
2. **Intent parsing** — Gemini extracts app purpose, user flows, required screens, and tone/style tokens.
3. **Layout + component synthesis** — drafts an information architecture, picks patterns (nav, lists, detail panels, forms), lays them out responsively.
4. **Visual styling** — applies typography, spacing, color, and states (Material-leaning defaults unless steered).
5. **Code rendering** — produces **HTML + CSS (Tailwind-utility style)** so each frame is a real rendered page, not a static mockup.
6. **Preview packaging** — each screen gets a `node-id` (ours: `13b5580c80f34bcabdfe3e8c8ec31a95`) so it can be shared as a live preview link.

<aside>

**Note:** The preview URL itself is gated behind an authenticated Stitch session, so its contents cannot be scraped externally. The pipeline above is Stitch's documented generation flow.

</aside>

## Milestone 2 — End-to-end workflow

### Phase 1 · Define intent (before opening Stitch)

- **App type** — e.g., internal dashboard, onboarding flow, admin console
- **Target user** — internal tool vs. consumer-facing
- **Key screens** — list them explicitly
- **Style anchors** — reference the [UI/UX guidelines](../UI%20UX%20guidelines%2020be6c5f913d4f53ac0e76eb5e904eef.md): ShadCN + Tailwind tokens from `globals.css`, semantic color, required states (loading / empty / error / success)

### Phase 2 · Generate in Stitch

1. Open Stitch → **New project** → select **Rapid mode** (required for Figma export; cannot be switched on later).
2. Paste the structured brief from Phase 1.
3. Iterate on the **infinite canvas** — drop images, text, or code as context; diverge with variants, then converge.
4. Refine screen-by-screen with targeted prompts (e.g., "add empty state to list view with CTA").

### Phase 3 · Export & hand off

| **Destination** | **How** |
| --- | --- |
| Figma (native frames) | Stitch → Figma plugin, or download `.zip` and run through [**html.to.design**](http://html.to.design) |
| Code | "Download" from the More menu → `.zip` of HTML/CSS |
| AI Studio / Antigravity | Direct export for dev handoff |
| Claude Code / Cursor | Feed exported code + `docs/design.md` token rules |

### Phase 4 · Integrate with governance

- **Notion SSOT** — log the Stitch preview link + exported artifacts on this page.
- **Figma** — map generated components onto the canonical library, replacing raw values with tokens.
- **Claude Design → Claude Code** — follow the flow on [6 · Workflow — Claude Design → Claude Code](../Workflow%20&%20Tooling/6%20%C2%B7%20Workflow%20%E2%80%94%20Claude%20Design%20%E2%86%92%20Claude%20Code%203474544eeb4281568702e4dd71f825a6.md) to convert exported UI into ShadCN + Tailwind production code.
- **Ship gate** — verify loading / empty / error / success states, contrast, focus ring, keyboard nav before sign-off.

<aside>
⚠️

**Gotcha:** If the project wasn't created in **Rapid mode**, the Figma export button will not appear. Re-generate in Rapid, or fall back to the `.zip` → [html.to.design](http://html.to.design) route.

</aside>

## Milestone 3 — Tie-in: `DESIGN.md` (open specification)

<aside>
📜

Google has **open-sourced the draft spec for `DESIGN.md`** ([announcement tweet](https://x.com/stitchbygoogle/status/2046624729403142320)) so the format Stitch uses to describe a design system — tokens, components, patterns, constraints — can be used across any tool or platform, not just Stitch.

</aside>

### Why it matters for this prototype

- **Phase 1 input** — a `DESIGN.md` file *is* the structured brief. Instead of a freeform prompt, feed Stitch tokens, component rules, and constraints in this format so outputs stay on-brand from generation 1.
- **Phase 3 hand-off** — `DESIGN.md` travels with the export, giving Figma, AI Studio, Claude Code, and Cursor the same source of truth.
- **Phase 4 governance** — aligns 1:1 with the `docs/design.md` file already owned under aosenuma UI/UX standards. Conforming to the open spec makes our rules **portable** to any AI design tool.

### Action items

- [ ]  Map existing `docs/design.md` tokens & components onto the open `DESIGN.md` spec
- [ ]  Version the resulting `DESIGN.md` in the repo alongside `docs/design-exceptions.md`
- [ ]  Use it as the Phase 1 input for every new Stitch project (paste or attach at project creation)
- [ ]  Add a check to the ship gate: exported artifact must reference the current `DESIGN.md` version