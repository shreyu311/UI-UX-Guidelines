# Instructions for AI assistants

This repository is a UI/UX design-guidelines and prototyping framework written in Markdown. When you generate or review interface designs or code with it:

1. **Read the rules:** [`DESIGN.md`](DESIGN.md). MUST rules are mandatory, SHOULD rules are defaults, MAY rules are optional.
2. **Read the brand book:** `brandbook/brandbook.md`, or the file the user names. If none exists, use the neutral fallbacks in `DESIGN.md` §3.4 and §3.5, and say so. The template, [`brandbook/brandbook.template.md`](brandbook/brandbook.template.md), is not a brand book; its `[PLACEHOLDERS]` mean "not provided".
3. **Apply precedence:** MUST rules → brand book values → SHOULD defaults → fallbacks (`DESIGN.md` §1).
4. **Never invent brand identity** (no names, logos, colors, fonts, or taglines that aren't in the brand book).
5. **Follow the workflow** in [`docs/prototyping-workflow.md`](docs/prototyping-workflow.md) and produce every applicable state.
6. **Self-check** against [`docs/validation.md`](docs/validation.md#review-checklist), then end with the report described in `DESIGN.md` AI-5: brand fields used, fallbacks applied, deviations by rule ID, and verified versus needs-a-human-check items.
7. **Don't modify** `DESIGN.md` or the brand book unless the user asks you to.
