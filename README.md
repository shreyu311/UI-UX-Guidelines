# UI/UX Guidelines

A brand-agnostic **design-guidelines and prototyping framework**. It gives designers, engineers, and AI design or coding assistants one set of rules for building consistent, accessible interfaces, and a separate brand book where each brand's values live.

Maintained by [@shreyu311](https://github.com/shreyu311) as a personal project.

---

## Why it exists

- **Prototypes drift.** Different people and tools produce different spacing, colors, and states for the same pattern.
- **AI tools improvise.** Without explicit rules they invent colors, skip states, and reach for generic defaults.
- **Brand values get scattered** across files, screenshots, and memory.
- **"Looks fine" isn't a review.** Teams need a checklist and a score, not opinions.

This framework addresses those problems with explicit rules, a configurable brand layer, and validation tools.

## How it works

| Layer | File | Contains |
| --- | --- | --- |
| **A. Core rules** | [`DESIGN.md`](DESIGN.md) | Principles, tokens, color, typography, layout, responsive behavior, components and states, interaction, navigation, content, accessibility (WCAG 2.2 AA), prototyping, and AI rules. The same for every brand. |
| **B. Brand book** | `brandbook/brandbook.md`, from [`brandbook/brandbook.template.md`](brandbook/brandbook.template.md) | Your brand's name, audience, voice, colors, fonts, logo, shape, density, and constraints. |

Precedence: **MUST rules → brand book → SHOULD defaults → neutral fallbacks.** A brand can set any visual value, but it can't weaken accessibility, usability, or responsive-design requirements. Values you haven't decided yet fall back to documented neutral defaults, rather than to an invented brand. Details: [`DESIGN.md` §1](DESIGN.md#1-how-the-core-rules-and-the-brand-book-work-together).

Principles: clarity over decoration, consistency over novelty, accessible by default, tokens instead of raw values, every state designed, one source of truth.

## What's included

| Path | Purpose |
| --- | --- |
| [`DESIGN.md`](DESIGN.md) | Core rules, with MUST / SHOULD / MAY levels and rule IDs |
| [`brandbook/`](brandbook/) | Brand book guide, fill-in template, and an assets folder |
| [`docs/prototyping-workflow.md`](docs/prototyping-workflow.md) | From requirement to reviewed prototype, including AI-assisted work |
| [`docs/validation.md`](docs/validation.md) | Review checklist, testing methods, scored audits |
| [`docs/customization.md`](docs/customization.md) | Adding tokens and components, changing rules, versioning, using it in a product repository |
| [`templates/`](templates/) | Audit scorecard and exception log |
| [`examples/`](examples/) | A fictional brand book, worked through end to end |
| [`AGENTS.md`](AGENTS.md) | Short instructions for AI assistants |

This repository contains documentation and templates only. There's no code generator, component library, linter, or build step.

---

## Quick start

1. **Get the files**

   ```bash
   git clone https://github.com/shreyu311/UI-UX-Guidelines.git
   cd UI-UX-Guidelines
   ```

2. **Create your brand book**

   ```bash
   cp brandbook/brandbook.template.md brandbook/brandbook.md
   ```

   Fill in what you know; leave the rest as placeholders. See [`brandbook/README.md`](brandbook/README.md).

3. **Write a prototype brief** using the template in [`docs/prototyping-workflow.md`](docs/prototyping-workflow.md#1-write-a-prototype-brief).

4. **Build the prototype**, by hand or with an AI assistant. Give the assistant `DESIGN.md`, your brand book, and the brief; there's a prompt template in the workflow guide.

5. **Validate** with the [review checklist](docs/validation.md#review-checklist) before sharing. Use the [scorecard](templates/scorecard.md) for periodic audits.

## Customizing and extending

Brand changes go in the brand book; rule changes go in `DESIGN.md` through a documented process, with semantic versioning. See [`docs/customization.md`](docs/customization.md).

## Contributing

Suggestions and corrections are welcome. See [`CONTRIBUTING.md`](CONTRIBUTING.md).

## License

[MIT](LICENSE)
