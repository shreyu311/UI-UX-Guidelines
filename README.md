# UI/UX Guidelines — open template

An **open, forkable UI/UX guideline library** any company can adopt and customize. Markdown-first so it renders on **GitHub**, pairs with **Figma** semantic variables, and feeds **AI coding tools** via [`AGENTS.md`](AGENTS.md) and [`DESIGN.md`](DESIGN.md).

**Start customizing:** [`CUSTOMIZATION.md`](CUSTOMIZATION.md) · **Your brand values:** [`BRANDBOOK.md`](BRANDBOOK.md)

---

## Quick start

| Step | Action |
| --- | --- |
| 1 | Fork this repo into your organization |
| 2 | Fill in [`BRANDBOOK.md`](BRANDBOOK.md) with your company colors, fonts, and logo rules |
| 3 | Add your logo to [`assets/`](assets/) |
| 4 | Update [`DESIGN.md`](DESIGN.md) with your resolved token values |
| 5 | Share with your design and engineering teams |

---

## Canonical entry (start here)

| Role | Document |
| --- | --- |
| **Your brand values** | [`BRANDBOOK.md`](BRANDBOOK.md) |
| **Humans — full narrative + tables** | [`UI UX Guidelines/UI UX guidelines`](UI%20UX%20Guidelines/UI%20UX%20guidelines%2020be6c5f913d4f53ac0e76eb5e904eef.md) |
| **Machines — agents** | [`AGENTS.md`](AGENTS.md) |
| **Machines — codegen excerpt** | [`DESIGN.md`](DESIGN.md) |
| **How to customize** | [`CUSTOMIZATION.md`](CUSTOMIZATION.md) |

---

## Source-of-truth ladder

When two files disagree:

1. **BRANDBOOK.md** — your company's brand identity (colors, fonts, logo, voice).
2. **Hub** (`UI UX guidelines …md`) — authoritative UI/UX summary referencing your brandbook tokens.
3. **Standards** [`UI UX Guidelines/Standards/`](UI%20UX%20Guidelines/Standards/) — binding detail for tokens, patterns, accessibility.
4. **Process & Governance** — how to ship, exceptions, playbooks (adapt to your org).

---

## Folder map

| Path | Purpose |
| --- | --- |
| [`BRANDBOOK.md`](BRANDBOOK.md) | **Your brand** — colors, fonts, logo, voice |
| [`assets/`](assets/) | Logo, brandbook PDF, favicon |
| [`UI UX Guidelines/Standards/`](UI%20UX%20Guidelines/Standards/) | Numbered binding chapters |
| [`UI UX Guidelines/Workflow & Tooling/`](UI%20UX%20Guidelines/Workflow%20%26%20Tooling/) | Tool workflows (Claude, Figma, Stitch) |
| [`UI UX Guidelines/Process & Governance/`](UI%20UX%20Guidelines/Process%20&%20Governance/) | Shipping, exceptions, governance |
| [`DESIGN.md`](DESIGN.md) | Compressed rules for AI codegen |
| [`AGENTS.md`](AGENTS.md) | Agent entry contract |

---

## Using this inside an application repository

Point your app's `docs/design.md` at anchored sections via permalinks, or add this repo as a git submodule. Preserve **semantic token names** in code (`globals.css`, Tailwind, Figma variables) — swap values in `BRANDBOOK.md`, not names in code.

---

## Contributing

See [`CONTRIBUTING.md`](CONTRIBUTING.md). Improvements to the **template structure** are welcome via PR. Keep your brand-specific values in your fork only.
