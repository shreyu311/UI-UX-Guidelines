# Prototyping workflow

How to turn a requirement into a reviewed prototype, by hand or with an AI assistant. The rules referenced here (for example `PRO-3`) are defined in [`../DESIGN.md`](../DESIGN.md).

```
Requirement → 1 Brief → 2 Flow and screens → 3 Fidelity → 4 Build → 5 States and sizes → 6 Validate → 7 Review and iterate
```

---

## 1. Write a prototype brief

A brief turns a requirement into something you can build and review. Copy this into your project:

```markdown
## Prototype brief: [NAME]

- Brand book: brandbook/brandbook.md   (or: none, use fallbacks)
- Requirement: As a [type of user], I want [goal] so that [reason].
- Acceptance criteria:
  - [CRITERION]
- Users and context: [who, which devices, environment, accessibility needs]
- Scope: in scope [FLOWS]; out of scope [FLOWS]; front-end only? [YES/NO]
- Screens and flows: [LIST]
- Content and data: [what real content looks like; the fictional sample data you'll use]
- States to show: default, empty, loading, error, success, [OTHERS]
- Edge cases: [long text, no permission, slow network, zero results, ...]
- Locale and accessibility: [locale; any requirement beyond the baseline]
- Constraints: [technical, legal, deadline]
- Fidelity: [wireframe / interactive / high-fidelity]
- Review question: [what reviewers must be able to decide after seeing it]
```

A brief is ready when every line has an answer, even if the answer is "not applicable".

## 2. Map the flow and screens

1. Write the main path as numbered steps from the user's point of view.
2. Add branches: errors, empty data, missing permission, slow or failed loading, cancel and undo.
3. List the screens:

| Screen | Purpose | Requirement it serves | Primary action | States |
| --- | --- | --- | --- | --- |
| `[SCREEN]` | `[PURPOSE]` | `[CRITERION]` | `[ACTION]` | `[STATES]` |

4. Place each screen in the navigation: page title (NAV-2), where it sits in the menu (NAV-1, NAV-3), and whether it needs breadcrumbs (NAV-6).

## 3. Choose the fidelity

Pick the lowest fidelity that answers the review question.

| Fidelity | Use it to decide | Rules that apply |
| --- | --- | --- |
| Wireframe | Structure, content priority, flow | Grayscale is fine; label it as a wireframe (PRO-8) |
| Interactive prototype | Flow, interaction, states | Tokens and documented components (PRO-2); states (PRO-3) |
| High-fidelity prototype | Visual design, brand fit, final content | Everything in `DESIGN.md`, brand book applied |

## 4. Build

- Define token values once and reference them everywhere else (TOK-1, AI-2). Brand book values enter only through tokens (BRD-3).
- Compose from documented components before creating new ones (CMP-1).
- Use realistic but fictional content: invented names, plausible numbers, real-length text (PRO-4).
- Label the prototype with fidelity and scope, for example "Interactive prototype · front-end only · fictional data" (PRO-1).
- For front-end-only prototypes, simulate data with static sample data and say which parts are simulated.

## 5. Cover states and sizes

For every screen, check:

- [ ] each state listed in the brief, using the state matrix in `DESIGN.md` §8.2 (PRO-3)
- [ ] the smallest and largest target sizes, at least 320 px and 1440 px wide (PRO-5, RSP-4)
- [ ] a complete keyboard path through the flow (A11Y-2)
- [ ] behavior with reduced motion turned on (INT-2)

## 6. Validate

Run the review checklist in [`validation.md`](validation.md#review-checklist). Fix every failed MUST item before sharing the prototype as "ready for review" (PRO-7). Record SHOULD deviations and their reasons.

## 7. Review and iterate

- Review against the brief's review question and acceptance criteria.
- Record decisions in the brief so the next iteration starts from them.
- When you had to guess because a rule was missing or unclear, propose a change to the rules ([`customization.md`](customization.md#changing-a-rule)). Fix the rule, not only the prototype.

---

## Working with AI assistants

The framework is plain Markdown, so any AI design or coding assistant that accepts files or long prompts can use it. This repository doesn't include a plugin or integration; you give the files to the tool.

### Context to provide, in this order

1. [`DESIGN.md`](../DESIGN.md), the rules
2. `brandbook/brandbook.md`, or a sentence saying there's no brand book
3. the prototype brief
4. optionally, your project's existing token file and components

Tools that read an instructions file automatically can use [`AGENTS.md`](../AGENTS.md).

### Prompt template

```text
You are building a [FIDELITY] prototype.

Follow DESIGN.md for the rules and brandbook/brandbook.md for brand values.
MUST rules override everything. Never invent brand values: use the fallbacks
in DESIGN.md sections 3.4 and 3.5 and list each one you used.

Task:
[PASTE THE PROTOTYPE BRIEF]

Deliver:
1. One token block (CSS custom properties) containing every value you use.
2. These screens: [SCREENS], each with these states: [STATES].
3. A report: brand fields used, fallbacks applied, rule deviations by ID,
   and which checklist items you verified versus which need a human check.
```

### Reviewing AI output

| What you see | Rule | What to ask for |
| --- | --- | --- |
| Hex codes or pixel values scattered through the code | TOK-1, AI-2 | Move every value into the token block and reference tokens |
| Only the default state | CMP-2, AI-4 | List the missing states explicitly |
| An invented logo, tagline, or brand color | BRD-2 | Use the brand book or the fallback, and say which |
| Clickable `div` elements instead of buttons or links | CMP-3, A11Y-7 | Use native elements |
| Placeholder text instead of labels | CNT-3 | Add visible labels |
| Light gray text on white | CLR-1 | Use `color.text.muted` or darker |
| "Submit" or "Click here" labels | CNT-1 | Labels that describe the action |
| The report says screen-reader testing passed | AI-6 | Mark it as "needs a human check" |

If the same problem keeps coming back, tighten the prompt or the rule text instead of fixing each output by hand.

### Using prototypes to test the rules

Building a handful of representative screens, such as a dashboard, a form, a settings page, and an empty state, using only the documented tokens and components is a quick way to find gaps in the rules. Wherever you have to guess, the rules are incomplete; add what's missing through the change process.

---

## Worked example (fictional)

**Requirement:** "As a member of a book club, I want to RSVP to the next meeting so that the host knows how many people are coming."

| Screen | Purpose | Primary action | States |
| --- | --- | --- | --- |
| Meeting details | Show the date, place, and seats left | RSVP | loading, load error, meeting full, already RSVP'd |
| RSVP confirmation | Confirm the response | Add to calendar | submitting, submit error, success |

Notes from applying the rules:

- The RSVP choice is a group of radio buttons with a visible legend ("Are you coming?"), not color-coded chips (CLR-2, A11Y-5).
- "Meeting full" appears as a warning banner with text, not a disabled button with no explanation (8.2: Disabled).
- The success message is announced to screen readers and focus moves to the confirmation heading (A11Y-5).
- Sample data uses invented names and a fictional venue (PRO-4).
