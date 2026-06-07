# Company UI/UX standards (shared)

This repository is the **shared UI/UX guideline library** for all projects — Markdown-first so it renders on **GitHub**, pairs with **Figma** semantic variables, and feeds **Claude Design / Claude Code / Cursor** via [`AGENTS.md`](AGENTS.md) and **Google Stitch** via root [`DESIGN.md`](DESIGN.md).

Quick map of long paths vs hashes: **`NAVIGATION.md`**. How we accept changes: **`CONTRIBUTING.md`**. Licensing: **`LICENSE`**.

---

## Canonical entry (start here)

| Role | Document |
| --- | --- |
| **Humans — full narrative + tables** | [`UI UX Guidelines/UI UX guidelines 20be6c5f913d4f53ac0e76eb5e904eef.md`](UI%20UX%20Guidelines/UI%20UX%20guidelines%2020be6c5f913d4f53ac0e76eb5e904eef.md) |
| **First-week onboarding (program)** | [`Onboarding — start here`](UI%20UX%20Guidelines/Planning%20%26%20Meetings/Company%20UI%20UX%20standards/Onboarding%20%E2%80%94%20start%20here%203454544eeb428192b340d7326b5015d4.md) (under Planning / Company UI UX standards) |
| **Machines — agents** | [`AGENTS.md`](AGENTS.md) |
| **Machines — Stitch excerpt** | [`DESIGN.md`](DESIGN.md) |

---

## Source-of-truth ladder (resolve conflicts here)

When two files disagree:

1. **Hub** (`UI UX guidelines 20be6c…md`) — authoritative summary: semantic palette, gradients, branding, pointers.
2. **Numbered Standards** [`UI UX Guidelines/Standards/`](UI%20UX%20Guidelines/Standards/) — binding detail for tokens, patterns, accessibility, assets (when cited by hub).
3. **`Process & Governance/`** — how to ship, exceptions logs, mandated reporting/playbooks.

**Planning & Meetings / Company UI UX standards:** onboarding templates, rollout notes, duplicated topic pages for **squads kicking off**. If text conflicts with **hub + Standards**, align Planning copy toward Standards rather than retaining a divergent fork.

---

## Pilot & project artifacts (**not** binding by default)

**[`UI UX Guidelines/Projects/`](UI%20UX%20Guidelines/Projects/README.md)** contains pilots, Stitch outputs, screenshots, HTML, and experiments. **`DESIGN.md` files nested under Projects are product-local** unless you explicitly promoted rules into **`Standards/`**. Always prefer repository root **[`DESIGN.md`](DESIGN.md)** for org-wide codegen.

---

## External links & Notion

Some pages retain **`notion.so`** references for stakeholder context, approvals, embedded boards, or live collaboration. Critical rules that must survive **offline / GitHub-only** workflows should ultimately be mirrored in this repo—but until then, broken Notion URLs are treated as governance debt; note URL moves in **`CONTRIBUTING.md`** PR checklist.

---

## Folder map

| Path | Purpose |
| --- | --- |
| [`UI UX Guidelines/`](UI%20UX%20Guidelines/UI%20UX%20guidelines%2020be6c5f913d4f53ac0e76eb5e904eef.md) | Hub, chapters, exports |
| [`Standards/`](UI%20UX%20Guidelines/Standards/) | Numbered binding chapters |
| [`Workflow & Tooling/`](UI%20UX%20Guidelines/Workflow%20%26%20Tooling/) | Consolidation · Claude loop · catalogs |
| [`Projects/`](UI%20UX%20Guidelines/Projects/README.md) | Pilots · prototypes |
| **`DESIGN.md`** (repo root) | Compressed rules for Stitch / agents — [**refresh**](UI%20UX%20Guidelines/Workflow%20%26%20Tooling/9%20%C2%B7%20Consolidation%20map%20%E2%80%94%20Notion%20%C2%B7%20Repo%20%C2%B7%20Stitch%20%C2%B7%20F%2034a4544eeb4281b5a45bd1d1321b52bf.md) when tokens flip |
| **`AGENTS.md`** | Claude / Cursor entry contract |

---

## Using this inside an application repository

Point **squads’ `docs/design.md`** at anchored sections via permalinks, or subtree / submodule checkout. Preserve **semantic token names** in code (`globals.css`, Tailwind, Figma matching variables).

---

## GitHub ergonomics & governance

Paths include spaces and punctuation; **`NAVIGATION.md`** exposes stable anchors. **`CODEOWNERS`** is stubbed comment-only under [`.github/`](.github/CODEOWNERS) — uncomment with your teams. **`LICENSE`** asserts internal proprietary default; substitute org counsel text if publishing publicly.
