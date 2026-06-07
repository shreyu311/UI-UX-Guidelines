# Experience principles

## How to use principles

Principles resolve disagreements. In conflict, **accessibility and user safety win** over visual novelty.

## 1. Clarity over cleverness

Users should understand screens without decoding jargon or layout tricks.

- **Do:** plain language, obvious hierarchy, predictable placement.
- **Don't:** cute labels that obscure outcomes, hidden affordances.

## 2. Efficiency with guardrails

Optimize for task completion; never sacrifice informed consent or reversibility.

- **Do:** smart defaults, progressive disclosure, batch actions when safe.
- **Don't:** dark patterns, irreversible actions without confirmation.

## 3. Consistency builds trust

Reuse tokens and patterns so muscle memory transfers across products.

- **Do:** same component for the same job; same words for the same concepts.
- **Don't:** one-off buttons or divergent terminology per squad.

## 4. Inclusive by default

Design for keyboard, screen readers, color blindness, motion sensitivity, and global audiences.

- **Do:** semantic structure, focus order, reduced motion, meaningful alt text.
- **Don't:** color-only status; auto-playing motion; tiny touch targets.

## 5. Calm feedback

Surfaces should acknowledge state: loading, success, empty, and recoverable errors.

- **Do:** specific errors with next steps; skeletons for slow loads.
- **Don't:** silent failures; generic "Something went wrong" only.

## 6. Respect for attention

Every interruption has a cost; earn the right to notify.

- **Do:** batch non-urgent updates; inline validation.
- **Don't:** stacked modals; noisy toasts for expected outcomes.

## 7. Evidence over opinion

Prefer research, analytics, and accessibility audits to taste debates.

- **Do:** tie decisions to principles + data; document exceptions in Governance.
- **Don't:** endless rework without a hypothesis.
- When principles conflict (example)
    
    **Efficiency** wants fewer steps; **clarity** wants explicit confirmation for deleting an account. **Outcome:** require confirmation and plain-language consequence — safety and clarity win.