# 9 · Consolidation map — Notion · Repo · Stitch · Figma

<aside>
📌

**Purpose:** One place to see **where the truth lives**, what to **duplicate** vs **link**, and how to stay aligned when specs live in Notion, code, Google Stitch, and Figma.

</aside>

## The core idea

You are not merging four unrelated docs — you are maintaining **one design system** with **four surfaces**. Each surface has a job:

| Surface | Job | Binding? |
| --- | --- | --- |
| **Notion (this hub + ch. 1–6)** | Human-readable spec, governance, review bar, links to Figma proof | **Yes** for product + design decisions |
| **Repo (`design.md`  • `docs/design/*`  • `globals.css`)** | What engineers implement; tokens in CSS; PR checklist | **Yes** for shipped UI behavior |
| **`DESIGN.md` (agent file for Stitch / tools)** | Compressed, generator-friendly rules: tokens, variants, guardrails | **Derived** from Notion + repo — not a third opinion |
| **Figma library** | Visual proof, components, Dev Mode; mirrors token names | **Yes** for pixels + component anatomy |
- **Rule of thumb: one authority per decision type**
    - **Color semantics** (what red means): **Notion semantic table** → mirrored in **`globals.css`** → repeated in **`DESIGN.md`** for agents.
    - **Exact hex / HSL values**: **`globals.css`** is what ships; Notion + Figma document the same values.
    - **Component states** (hover, focus, disabled): **Figma matrices** + **Notion ch. 4** → **ShadCN** in repo.
    - **Process** (exceptions, shipping checklist): **Notion ch. 5** only — don’t fork process into Stitch.

## What to consolidate (copy) vs connect (link)

| Content | Consolidate how? | Why |
| --- | --- | --- |
| Semantic palette + “never use red for…” | **Copy** short tables into `DESIGN.md`; **link** full psychology to Notion | Agents need the table; humans need context |
| Button matrix → ShadCN variants | **Copy** the mapping table to repo + `DESIGN.md` | Prevents drift at codegen |
| Spacing / radius / type scale | **Single numbers** in repo tokens; Notion **links** to Figma swatches | Avoid three different “sources of px” |
| Full engineering appendix (Tailwind, a11y, z-index) | Keep in **`docs/design.md`** (or split files); Notion hub **links** to repo paths | Long spec belongs with code |
| Embedded Figma / PNG proof | **Link only** in Notion; don’t paste huge galleries into `DESIGN.md` | Stitch doesn’t need pixels; people do |

## Suggested folder / file shape (repo)

- **`design.md`** or **`docs/design.md`** — short hub + links into `docs/design/…`
- **`docs/design/3-tokens.md`** — semantic roles ↔ CSS vars (what you already sketched)
- **`docs/design/6-components.md`** — button matrix, patterns
- **`docs/design-exceptions.md`** — approved deviations
- **`DESIGN.md` at repo root** (optional) — **Stitch-optimized** excerpt: tokens, variants, guardrails, 1-page max; regenerate when Notion or `globals.css` changes

## Sync rhythm (keep consolidation honest)

- [ ]  **When tokens change:** update `globals.css` first → update Notion semantic table → refresh `DESIGN.md` → flag Figma variables
- [ ]  **When a pattern is new:** add to Notion ch. 4 + Figma → implement in ShadCN → add PR checklist item if needed
- [ ]  **When a tool breaks a rule:** log in **`docs/design-exceptions.md`** (screenshot + rationale), not only in chat

## Google Stitch specifically

Stitch’s **`DESIGN.md`** is an **import/export** format for design rules — treat it as a **projection** of this hub, not a competing doc.

- **What to put in Stitch `DESIGN.md`**
    1. Semantic colors + gradient rule (135°, teal ramp)
    2. ShadCN variant names for buttons (primary / secondary / ghost / destructive)
    3. 8pt grid + key spacing (e.g. CTA horizontal **32px**, touch **≥ 44×44**)
    4. Radius baseline (**12px** / `--radius`)
    5. Guardrails: **no orphan hex** in shipped UI; **semantic red** only for destructive/errors
    6. “Reject” instructions for the agent (e.g. if output uses raw hex, fix before handoff)
- **What stays in Notion only**
    - Governance, owners, pilot plan, stakeholder process
    - Long narrative and Figma embeds
    - Exception workflow and compliance narrative

## Quick decision tree

**Did the change affect a CSS variable or Tailwind class?** → Repo first, then Notion table, then `DESIGN.md`.

**Did the change affect how something should look in pixels?** → Figma + Notion ch. 3/4, then repo components.

**Did the change affect process only?** → Notion ch. 5 only.

## Related pages

- [UI/UX guidelines](../UI%20UX%20guidelines%2020be6c5f913d4f53ac0e76eb5e904eef.md) — parent hub
- [6 · Workflow — Claude Design → Claude Code](6%20%C2%B7%20Workflow%20%E2%80%94%20Claude%20Design%20%E2%86%92%20Claude%20Code%203474544eeb4281568702e4dd71f825a6.md) — workflow chapter
- [5 · Governance & shipping](../Process%20&%20Governance/5%20%C2%B7%20Governance%20&%20shipping%203454544eeb4281808c68e067d0b6a0f7.md) — governance & shipping

## Owner / next step

- **You:** Pick a single **`DESIGN.md`** owner (file in repo) and add a calendar reminder to **diff** it whenever `globals.css` changes.
- **Team:** Agree that **PRs** reference either Notion section or `docs/design/…` path — not screenshots in Slack as the spec.