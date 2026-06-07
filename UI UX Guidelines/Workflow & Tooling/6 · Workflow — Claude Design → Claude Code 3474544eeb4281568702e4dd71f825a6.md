# 6 · Workflow — Claude Design → Claude Code

<aside>
**Operating loop** for the [YOUR_COMPANY_NAME] design system. **Claude Design** (Anthropic, research preview — Apr 2026) is the **conversational front-end** between a brief and shipped code. This page does **not** replace the hub or the Figma library; it sits **between brief and code** and is **bound** by the same tokens, states, semantic color, and governance defined in chapters 1 → 5 of [UI/UX guidelines hub](UI%20UX%20guidelines%2020be6c5f913d4f53ac0e76eb5e904eef.md).

</aside>

## TL;DR

- **Briefs** (ch. 1) → **Claude Design** generates against the onboarded **[YOUR_COMPANY_NAME]** system (ch. 2) → reviewers refine against state matrices (ch. 4) and visual proof (ch. 3) → **one-command handoff to Claude Code** for ShadCN-first implementation (ch. 5) → frames **mirrored back** into the **canonical Figma library** so design, code, and Notion stay one system.
- **Status:** research preview. Treat Claude Design as **assistive**; the hub + Figma library remain **binding**.
- **Owner:** [YOUR_NAME] (UI/UX Standards Owner).

## Why this exists

Claude Design (launched Apr 2026, research preview) generates UI from natural language, can analyze a codebase + design files to **infer a custom design system**, and ships finished frames to **Claude Code** with one command. Without explicit guardrails, an AI design tool will drift into generic blue / Material UI defaults. This page binds Claude Design to the **[YOUR_COMPANY_NAME] standard** so its output is shippable from day one.

## Inputs — single source of truth

| Source | What it provides | Reference |
| --- | --- | --- |
| **Spec hub** | Entry, principles, semantic color (non-negotiable), buttons-at-a-glance | [UI/UX guidelines hub](UI%20UX%20guidelines%2020be6c5f913d4f53ac0e76eb5e904eef.md) |
| **Ch. 1 — Scope & principles** | UI element inventory, *New project / new frame checklist (Apr 14 baseline)* | [1 · Scope & principles](../Standards/1%20%C2%B7%20Scope%20&%20principles%203454544eeb42810c89b3d3e4ef563c43.md) |
| **Ch. 2 — Brand, layout & tokens** | Semantic palette, gradient (135° **[YOUR_PRIMARY_DARK] → [YOUR_PRIMARY]**), typography, 8pt grid, radius, shadows, *Visual swatches* | [2 · Brand, layout & tokens](../Standards/2%20%C2%B7%20Brand,%20layout%20&%20tokens%203454544eeb4281ce92bbf7eb90df3835.md) |
| **Ch. 3 — Style Card for UI/UX** | *Embedded pattern gallery* — visual proof for hero, chrome, cards, CTAs, accent discipline | [3 · Style Card for UI/UX](../Standards/3%20%C2%B7%20Style%20Card%20for%20UI%20UX%203454544eeb428013a31df04ad5caa2e2.md) |
| **Ch. 4 — Components & patterns** | Authoritative button state matrix, accessibility, content rules | [4 · Components & patterns](../Standards/4%20%C2%B7%20Components%20&%20patterns%203454544eeb4281479040ce5bd99406c7.md) |
| **Ch. 5 — Governance & shipping** | PR checklist, exceptions log, sign-off | [5 · Governance & shipping](../Process%20&%20Governance/5%20%C2%B7%20Governance%20&%20shipping%203454544eeb4281808c68e067d0b6a0f7.md) |
| **Code** | `globals.css`  • ShadCN/Tailwind primitives (token names must match in design) | repo |
| **Figma library** | Canonical mirror of tokens + components | (link in ch. 2 once published) |

## Visual: the loop at a glance

```mermaid
flowchart LR
	A["📥 Brief"] --> B["🎨 Generate"]
	B --> C["🔍 Review"]
	C --> D["🚀 Code"]
	D --> E["🔁 Figma"]
	E -.-> A
```

1. 📥 **Brief** — write the ask
2. 🎨 **Generate** — Claude Design creates frames
3. 🔍 **Review** — check tokens, states, a11y
4. 🚀 **Code** — hand off to Claude Code
5. 🔁 **Figma** — mirror back to the library

## The loop — step by step

### 0 · Onboard Claude Design (one-time per project)

**Goal:** make Claude Design speak [YOUR_COMPANY_NAME], not generic UI-kit blue.

- Point Claude Design at the **repo** so it learns ShadCN + Tailwind variants and reads `globals.css` token names.
- Upload (or link) the hub + chapters **2 · Brand, layout & tokens** and **4 · Components & patterns** so the inferred system mat