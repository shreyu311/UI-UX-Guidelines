# Customizing and extending

How to adapt the framework without mixing brand values into the core rules.

---

## Where each change belongs

| You want to | Edit | Don't edit |
| --- | --- | --- |
| Apply your brand | `brandbook/brandbook.md` ([setup](../brandbook/README.md)) | `DESIGN.md` |
| Deviate from a SHOULD default for your brand | The brand book's "Constraints and exceptions" section | `DESIGN.md` |
| Change a core rule for everyone using your copy | `DESIGN.md`, following "Changing a rule" below | |
| Record a one-off deviation for a screen or release | Your copy of [`templates/exception-log.md`](../templates/exception-log.md) | `DESIGN.md` |
| Tell an AI tool how to use these files | [`AGENTS.md`](../AGENTS.md) | |

---

## Adding a token

1. Check that no existing token already expresses the need.
2. Name it by purpose using `{category}.{role}.{variant}.{state}` (TOK-3).
3. Add it in the right place:
   - **core tokens** every brand needs: `DESIGN.md` §3, with a neutral fallback value;
   - **brand-only tokens**, such as an accent or gradient: the brand book, next to the value.
4. Record it in [`CHANGELOG.md`](../CHANGELOG.md) as a minor change.

## Adding a component

1. Confirm that no existing component covers the need (CMP-1).
2. Write a spec with the structure in `DESIGN.md` §8.1: purpose, anatomy, variants, sizes, states, behavior, content, accessibility, do and don't.
3. Define every applicable state from the state matrix (§8.2).
4. Keep the spec where the rest of your specs live: a short entry in `DESIGN.md` §8.3, or a `components/` folder in your copy once there are many.
5. Have it reviewed from both a design and an engineering perspective, then record it in the changelog.

## Changing a rule

- **SHOULD and MAY rules:** update the wording, write down the reason, and record a minor or patch change.
- **MUST rules** encode accessibility and usability baselines. Making one stricter is a minor change. Weakening or removing one is a major change and should be rare; never go below WCAG 2.2 AA.
- **Rule IDs** stay stable. Retire an ID rather than reusing it for a different rule.

## Recording exceptions

Copy [`templates/exception-log.md`](../templates/exception-log.md) into your project. Every exception needs an owner, a reason, the rule ID it deviates from, and an expiry or review date. A deviation that keeps coming back is a sign the rule should change instead.

---

## Versioning

Use semantic versioning for `DESIGN.md` and record every change in the changelog:

| Change | Version bump |
| --- | --- |
| Renamed or removed tokens; weakened or removed MUST rules | Major |
| New tokens, rules, or components; stricter rules | Minor |
| Clarifications and fixes that don't change meaning | Patch |

Update the version line at the top of `DESIGN.md` at the same time.

## Keeping your copy up to date

If you forked or cloned this repository, you can pull in later improvements:

```bash
git remote add upstream https://github.com/shreyu311/UI-UX-Guidelines.git
git fetch upstream
git merge upstream/main
```

Your brand book won't conflict, because the upstream repository only contains the template.

---

## Using the framework in a product repository

- Copy `DESIGN.md` and your brand book into the product's documentation (for example `docs/design/`), or add this repository as a Git submodule.
- Keep implementation values in **one** token file in code (for example `tokens.css` or `tokens.json`) that mirrors the brand book and the fallbacks.
- Keep **one authority per decision**:

  | Decision | Authority |
  | --- | --- |
  | Rules and their levels | `DESIGN.md` |
  | Brand values | The brand book |
  | Values used by the code | The token file, which mirrors the two above |
  | Tool-specific rule files (for example, an AI tool's instructions) | Derived copies: regenerate them when the sources change; never edit them on their own |

- Point your AI tools to these files through `AGENTS.md` or the tool's equivalent.

## Team adoption (optional)

If several people maintain the framework, agree on who does what:

| Activity | Standards owner | Design | Engineering | Product |
| --- | --- | --- | --- | --- |
| Maintain `DESIGN.md` and tokens | Accountable | Responsible | Consulted | Informed |
| Approve new components | Accountable | Responsible | Responsible | Consulted |
| Run scored audits | Accountable | Responsible | Consulted | Informed |
| Approve exceptions | Accountable | Consulted | Consulted | Responsible |
| Fix failures in a product | Informed | Responsible | Responsible | Accountable |
