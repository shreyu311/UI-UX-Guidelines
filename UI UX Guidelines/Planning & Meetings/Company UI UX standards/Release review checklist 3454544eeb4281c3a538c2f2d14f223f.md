# Release review checklist

## UX / UI launch checklist

Copy into a ticket or PR.

### Foundations

- [ ]  Uses **design tokens** (no stray hex in components)
- [ ]  **Responsive** behavior checked at xs / md / xl
- [ ]  **Dark mode** checked if applicable

### Patterns

- [ ]  Correct **component** for the job; no duplicate patterns
- [ ]  **Empty, loading, error** states designed

### Accessibility

- [ ]  Keyboard path complete; focus visible
- [ ]  Contrast passes for text and critical icons
- [ ]  Screen reader labels for custom controls
- [ ]  Motion respects **prefers-reduced-motion**

### Content

- [ ]  **Verb-first** buttons; glossary terms respected
- [ ]  Errors explain **fix** not blame

### Governance

- [ ]  Linked Figma and Storybook references attached
- [ ]  **Standards changelog** updated if patterns/tokens changed