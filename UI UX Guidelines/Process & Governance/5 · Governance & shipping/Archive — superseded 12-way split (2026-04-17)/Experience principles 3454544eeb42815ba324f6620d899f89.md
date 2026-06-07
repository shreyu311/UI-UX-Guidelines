# Experience principles

> **Former location:** Part I — § 2 in the CTO hub.
> 

## Non-negotiable principles

- **Consistency over novelty:** reuse approved patterns and components before inventing new ones.
- **Clarity first:** hierarchy, labels, and whitespace must reduce cognitive load.
- **Accessibility baseline:** sufficient contrast, keyboard navigation, visible focus states.
- **States are mandatory:** loading, empty, error, and success must be designed and implemented.

## When principles conflict

Accessibility and **recoverability** (clear errors, safe destructive actions) take precedence over visual novelty or one-off layout experiments.

## AI-assisted workflows and tooling

- Keep tokens, rules, and patterns **explicit and machine-readable** so developers and AI-assisted tools apply the same constraints.
- Prefer **Figma** for UI specifications and token-accurate handoff into implementation.
- When layout, hierarchy, or interaction quality matters, capture **visual acceptance criteria** — not text-only substitutes.