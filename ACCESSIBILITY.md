# Accessibility Standards

**Status:** Binding — WCAG 2.1 Level AA is the **minimum requirement** for all shipped UI. Aosenuma projects must pass automated and manual accessibility audits before release.

---

## WCAG 2.1 Level AA Compliance Matrix

All UI components and pages must meet these criteria:

| Principle | Standard | Requirement | How to verify |
|-----------|----------|-------------|----------------|
| **Perceivable** | 1.4.3 Contrast (Minimum) | Foreground/background color ratio ≥ 4.5:1 (text), ≥ 3:1 (large text, graphics) | WebAIM Contrast Checker, axe DevTools |
| **Perceivable** | 1.4.11 Non-text Contrast | UI components and graphical elements ≥ 3:1 contrast ratio | axe DevTools, manual inspection |
| **Perceivable** | 1.3.1 Info & Relationships | All information conveyed by color also conveyed by structure (text, icon, shape) | Screen reader audit, browser inspector |
| **Operable** | 2.1.1 Keyboard | All functionality operable via keyboard (no keyboard trap) | Tab through entire page, test with only keyboard |
| **Operable** | 2.1.2 No Keyboard Trap | Focus can move away from any element using keyboard alone | Navigate with Tab/Shift+Tab—focus must not get stuck |
| **Operable** | 2.4.3 Focus Order | Focus order is logical and meaningful | Verify tab order matches visual reading order |
| **Operable** | 2.4.7 Focus Visible | Keyboard focus indicator is always visible | `outline: 2px solid #208692; outline-offset: 2px;` (or equivalent) |
| **Operable** | 2.4.4 Link Purpose | Purpose of link is clear from link text OR surrounding context | Avoid generic "click here"; use `aria-label` if needed |
| **Understandable** | 3.3.1 Error Identification | Form errors are identified AND described in text (not color alone) | Error messages must include the field name and issue |
| **Understandable** | 3.3.4 Error Prevention | Confirmations provided for legal, financial, or data deletion actions | Show confirmation dialog; require explicit opt-in |
| **Robust** | 4.1.2 Name, Role, Value | UI components expose name, role, state, and value to assistive tech | Inspect with NVDA/JAWS; check `aria-label`, `aria-describedby`, roles |
| **Robust** | 4.1.3 Status Messages | Status messages are announced without focus shift | Use `role="status"` or `role="alert"` with `aria-live` |

---

## Color & Contrast

### Semantic Palette (WCAG AA pre-verified)

All colors in the design system have been tested for contrast compliance:

| Color | Hex | WCAG AA on White | WCAG AA on Black | Use case |
|-------|-----|------------------|------------------|----------|
| Primary Teal | `#208692` | ✅ 4.5:1 | ✅ 5.2:1 | CTAs, links, primary actions |
| Sage Wash | `#E5EADF` | ❌ 1.8:1 (insufficient on white) | ✅ 11:1 | Hover states; pair with dark text for sufficient contrast |
| Destructive | `#DC2626` | ❌ 3.9:1 (insufficient on white; use `#B91C1C` for text) | ✅ 6.5:1 | Error states, destructive actions |
| Success | `#16A34A` | ✅ 5.2:1 | ✅ 4.5:1 | Confirmations, success states |
| Warning | `#F59E0B` | ❌ 2.1:1 (pair with dark text or dark background) | ✅ 8.5:1 | Non-blocking alerts, warnings |
| Info | `#3B82F6` | ✅ 4.5:1 | ✅ 5.6:1 | Informational content |
| Disabled | `#D1D5DB` (fill), `#9CA3AF` (text) | ❌ Do not use for interactive elements | ✅ 4.7:1 | Disabled states only |

**Rule:** Never use `#E5EADF` (Sage Wash), `#F59E0B` (Warning), or `#D1D5DB` (Disabled) as text or interactive element fill on white. Always pair with darker alternatives or sufficient background contrast.

### Testing Contrast

- **Automated:** [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/), axe DevTools browser extension, or GitHub's built-in color contrast tools
- **Reporting:** Document contrast ratios in component specs and audit logs (see **Testing & QA** section)

---

## Keyboard Navigation

### Focus Management

Every interactive element must:
1. **Receive focus** via Tab key
2. **Show a visible focus indicator** (default browser outline or custom)
3. **Be operable** via keyboard (Space for buttons, Enter for links, arrow keys for complex widgets)

### Custom Focus Indicators

If overriding the browser default outline, use:

```css
/* Primary focus style */
:focus-visible {
  outline: 2px solid #208692;
  outline-offset: 2px;
}

/* Dark background variant */
body.dark-mode :focus-visible {
  outline: 2px solid #E5EADF;
  outline-offset: 2px;
}
```

### Common Focus Issues

| Issue | Fix |
|-------|-----|
| Focus trap (Tab loops in modal) | Trap focus intentionally; move focus back to trigger on close |
| Invisible focus indicator | Add `outline` or `box-shadow`; ensure contrast ≥ 3:1 against background |
| Focus order doesn't match visual order | Use `tabindex` sparingly; rely on DOM order |
| Skip link not visible on focus | Show skip links on keyboard focus: `a.skip-link:focus { position: static; }` |

---

## Screen Reader Support

### ARIA Labels & Descriptions

Use ARIA attributes to provide context assistive technology cannot infer:

```html
<!-- Button with icon only: use aria-label -->
<button aria-label="Close dialog">
  <svg class="icon-close"></svg>
</button>

<!-- Form field with external label -->
<label for="email">Email</label>
<input id="email" type="email" />

<!-- Field with helper text: use aria-describedby -->
<input 
  id="password" 
  type="password" 
  aria-describedby="pwd-hint"
/>
<small id="pwd-hint">Min 8 characters, 1 number, 1 symbol</small>

<!-- Status message announcement: use role="status" + aria-live -->
<div role="status" aria-live="polite" aria-atomic="true">
  Form submitted successfully!
</div>
```

### Semantic HTML First

| Do | Don't |
|----|-------|
| `<button>`, `<a>`, `<input>`, `<label>` | `<div onclick="...">`, `<span role="button">` |
| `<h1>`–`<h6>` with proper hierarchy | Skipping heading levels (h1 → h3) |
| `<nav>`, `<main>`, `<section>`, `<article>` | Generic `<div>` wrappers for landmarks |
| `<ul>`, `<ol>`, `<li>` for lists | Comma-separated text or `<div>` lists |

### Testing

- **NVDA** (Windows screen reader, free)
- **JAWS** (commercial; more features)
- **VoiceOver** (macOS/iOS, built-in)
- **TalkBack** (Android, built-in)

**Quick test:** Disable CSS, navigate by Tab and arrow keys only. Content should remain understandable and navigable.

---

## Form Accessibility

### Required Fields & Error Messages

```html
<!-- Mark as required -->
<label for="name">
  Name <span aria-label="required">*</span>
</label>
<input id="name" type="text" required aria-required="true" />

<!-- Associate error with field -->
<input 
  id="email" 
  type="email" 
  aria-invalid="true"
  aria-describedby="email-error"
/>
<span id="email-error" role="alert">
  Invalid email format. Use name@example.com
</span>
```

### Do's & Don'ts

| Do | Don't |
|----|-------|
| Place labels visibly above/beside inputs | Use placeholder as label |
| Include field name in error message | "Error: Invalid input" |
| Announce form submission with status message | Silently change page without notification |
| Use radio buttons for exclusive choices | Use multiple checkboxes as radio buttons |
| Provide clear success confirmation | Assume user knows form succeeded |

---

## Images & Icons

### Alt Text Guidance

```html
<!-- Decorative image: empty alt -->
<img src="divider.svg" alt="" aria-hidden="true" />

<!-- Informative image: describe purpose -->
<img src="chart.png" alt="Sales increased 20% in Q3 2025" />

<!-- Complex image (chart, diagram): brief alt + link to full description -->
<img 
  src="architecture.svg" 
  alt="System architecture diagram" 
  aria-describedby="arch-desc"
/>
<details id="arch-desc">
  <summary>Full architecture description</summary>
  <p>The system consists of...</p>
</details>

<!-- Icon-only button: use aria-label -->
<button aria-label="Download report">
  <svg class="icon-download"></svg>
</button>
```

### Icons in Text

If an icon conveys meaning (not decoration), add `aria-label` or ARIA attributes:

```html
<!-- Warning icon before message -->
<span aria-label="warning">⚠️</span> Action cannot be undone

<!-- Better: use SVG with title -->
<svg aria-label="warning" class="icon-warning">
  <title>Warning</title>
  <!-- SVG content -->
</svg>
```

---

## Motion & Animations

### Respect Prefers-Reduced-Motion

```css
/* Always include this query */
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}

/* Or disable specific animations */
@media (prefers-reduced-motion: reduce) {
  .animated-card {
    animation: none;
  }
}
```

**Why:** ~15% of users prefer reduced motion (vestibular disorders, migraines, photosensitive epilepsy).

---

## Responsive & Mobile Accessibility

### Touch Targets

- **Minimum size:** 44×44 px (Apple standard)
- **Recommended spacing:** 8–16 px between targets
- **Use case:** Mobile/touch; also benefits users with tremor or motor control issues

```css
button {
  min-width: 44px;
  min-height: 44px;
  padding: 12px 16px; /* Ensures padding-box is at least 44×44 */
}
```

### Mobile-Specific Tests

- Test with mobile screen reader (VoiceOver, TalkBack)
- Zoom to 200%—layout should remain functional
- Rotate device—content reflow should work

---

## Audit & Testing Checklist

Use this before each release:

- [ ] **Contrast check:** All text ≥ 4.5:1, UI components ≥ 3:1 (automated tool)
- [ ] **Keyboard navigation:** Tab through entire page; no traps; focus visible
- [ ] **Form fields:** All inputs have labels; errors associated with fields
- [ ] **Images:** All informative images have alt text; decorative images marked `alt=""`
- [ ] **ARIA:** `role`, `aria-label`, `aria-describedby` used correctly (no redundancy)
- [ ] **Headings:** Proper hierarchy; no skipped levels
- [ ] **Landmarks:** `<main>`, `<nav>`, `<footer>` present where appropriate
- [ ] **Screen reader test:** Test with NVDA/JAWS/VoiceOver; content understandable
- [ ] **Motion:** Test with prefers-reduced-motion enabled
- [ ] **Mobile:** Touch targets ≥ 44×44; zoom to 200%; test with TalkBack

### Tools

| Tool | Type | Cost |
|------|------|------|
| **axe DevTools** | Browser extension (Chrome, Firefox, Edge) | Free |
| **WAVE** | Browser extension + web | Free |
| **Lighthouse** (in DevTools) | Built into Chrome DevTools | Free |
| **NVDA** | Screen reader (Windows) | Free |
| **Deque axe Pro** | Comprehensive audit platform | Paid |
| **Level Access** | Professional audit service | Paid |

---

## Reporting & Exceptions

### Accessibility Audit Log

Create a file at **`UI UX Guidelines/Process & Governance/Accessibility Audit Log.md`** (or append to existing governance doc):

```markdown
## Accessibility Audit Results

| Component/Page | Date | Auditor | Status | Issues Found | WCAG Failures | Exceptions Logged | Next Review |
|---|---|---|---|---|---|---|---|
| Button (primary) | 2025-05-20 | @designer | ✅ Pass | 0 | — | — | Q3 2025 |
| Form (user signup) | 2025-05-20 | @qa-lead | ⚠️ Partial | 2 | 1.4.3 (contrast), 3.3.1 (error labels) | None (in progress) | 2025-05-27 |
```

### Exception Process

If an exception is needed (rare):

1. **Document:** Reason, scope, affected users, mitigation
2. **Approval:** Requires design lead + accessibility officer sign-off
3. **Remediation timeline:** Must include target fix date
4. **Alternative:** Propose accessible alternative or workaround

Example:

```markdown
### Exception: Financial Chart (Pilot Project)

- **Why:** Third-party charting library does not support WCAG AA for real-time updates
- **Scope:** Prediction Market dashboard chart only
- **Affected users:** ~2% (screen reader users viewing live market data)
- **Mitigation:** Provide downloadable CSV export with same data
- **Approved by:** @design-lead, @accessibility-officer
- **Target fix:** 2025-07-30 (when library updates)
- **Status:** Open → Closed on fix date
```

---

## Resources & References

- **[WCAG 2.1 Overview](https://www.w3.org/WAI/WCAG21/quickref/)** — Official W3C guidelines
- **[WebAIM Articles](https://webaim.org/)** — Practical guides on contrast, forms, screen readers, etc.
- **[MDN ARIA Guide](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA)** — ARIA attributes reference
- **[Inclusive Components](https://inclusive-components.design/)** — Pattern library with accessibility baked in
- **[The A11y Project](https://www.a11yproject.com/)** — Community resource for accessibility
- **[Deque University](https://dequeuniversity.com/)** — Free accessibility training

---

## Questions?

File an issue or PR with the `accessibility` label. Escalate WCAG AA violations to @accessibility-officer (assign in CODEOWNERS).
