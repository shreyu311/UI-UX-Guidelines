# Components & patterns

## How to document a component

For each: **anatomy**, **variants**, **states**, **accessibility**, **content rules**, **when to use / avoid**, and **links** to Figma + Storybook.

## 1. Buttons

- **Variants:** primary, secondary, tertiary/ghost, destructive.
- **States:** default, hover, focus-visible, active, disabled, loading.
- **Content:** verb-first labels (`Save`, `Send invite`). Avoid `OK`/`Submit` when a specific verb works.

## 2. Forms and inputs

- **Validation:** inline on blur for optional; on submit for required groups.
- **Errors:** associate `aria-describedby`; show **what failed** and **how to fix**.
- **Required fields:** mark required; do not mark optional-only forms redundantly.

## 3. Navigation

- **Primary nav** items ≤ 7±2; current location visible.
- **Mobile:** overflow pattern documented (tabs, more menu, drawer).

## 4. Tables

- **Sortable** columns indicated; keyboard support.
- **Row actions** don't rely on hover-only affordances.

## 5. Modals and drawers

- **Focus trap** and **return focus** on close.
- **Widths:** max width for reading; full-screen drawer on small breakpoints if needed.

## 6. Notifications: toast, banner, inline

- **Toast:** transient, non-blocking, max stack policy.
- **Banner:** persistent system issues; dismiss rules documented.

## 7. Empty states

- **Illustration optional**; always include headline, short explainer, primary action.

## 8. Loading

- Prefer **skeletons** for known layouts; **spinners** for indeterminate short waits.

## 9. Search and filters

- **Clear** active filters; show result counts when costly.

## 10. Authentication patterns (if shared)

- Password rules, magic link copy, lockout messaging — keep **consistent and humane**.
- Pattern selection in review
    
    Ask: **Which user job?** **Which principle?** **Which token and component?** If no match, propose addition via Governance — avoid one-offs.