# Developer Handoff: Code Examples & API Specs

**Purpose:** Make component handoff from design to development frictionless and consistent. Required for promotion from Draft → Stable.

---

## Quick Start
- Every Stable component needs:
  - CSS/Tailwind usage examples
  - API documentation table (props, events)
  - Accessibility annotations
  - Migration sections for API changes or deprecations
  - Responsive and performance notes

_Link example handoff files in the Standards/ folder for actual component-specific details._

---

## Example — Button Component

### 1. Visual Spec (Design Token Reference)

- **Semantic tokens only** (no hex):
  - Background: `color-cta-primary`
  - Border: `border-cta-primary`, `border-width-1`
  - Text: `text-on-primary`
  - Hover: `color-cta-primary-hover`
- **Sizing:**
  - Height: 48px (large), 40px (default), 32px (small)
  - Padding: 0 32px (large), 0 24px (medium), 0 8px (small)

### 2. Tailwind/CSS Example

```html
<!-- Primary Button -->
<button class="bg-[[YOUR_PRIMARY]] text-white font-bold py-3 px-8 rounded-[12px] focus:outline-none focus-visible:ring-2 ring-offset-2 ring-[[YOUR_PRIMARY]] transition hover:bg-[[YOUR_PRIMARY_DARK]]">
  Confirm
</button>

<!-- Destructive Button -->
<button class="bg-[#DC2626] text-white py-3 px-8 rounded-[12px] hover:bg-[#B91C1C] focus:outline-none focus:ring-2 ring-[#DC2626]">
  Delete
</button>
```

### 3. Component API Spec

| Prop         | Type        | Required | Default    | Description                                  |
|--------------|-------------|----------|------------|----------------------------------------------|
| `variant`    | string      | Yes      | "primary"  | "primary", "secondary", "ghost", "destructive"|
| `size`       | string      | No       | "md"       | "sm", "md", "lg"                             |
| `disabled`   | boolean     | No       | false      | Disables interaction                         |
| `onClick`    | function    | Yes      | —          | Event handler for click                      |
| `aria-label` | string      | No       | —          | Accessible label for icon-only buttons       |

### 4. Accessibility Notes
- All focusable elements: `tabindex="0"` (unless naturally focusable)
- `:focus-visible` outline must be visible (default or custom ring)
- ARIA: `aria-label` for icon-only buttons
- Disabled: uses semantic styles, not `display:none`

### 5. Responsive Guidelines
- min-width: 44px; min-height: 44px (touch-able)
- On mobile: use `w-full` for main actions by default

---

## Example — Input Field

```html
<label for="email" class="block text-sm font-bold mb-1">Email</label>
<input
  type="email"
  id="email"
  class="block w-full p-3 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-[[YOUR_PRIMARY]]"
  aria-required="true"
  aria-describedby="email-help"
/>
<small id="email-help">We never share your email.</small>
```

| Prop         | Type        | Required | Default    | Description                                  |
|--------------|-------------|----------|------------|----------------------------------------------|
| `type`       | string      | Yes      | "text"     | input type: "text", "email", etc.            |
| `value`      | string      | Yes      | —          | controlled value property                    |
| `onChange`   | function    | Yes      | —          | handler for input change                     |
| `disabled`   | boolean     | No       | false      | disable input                               |
| `placeholder`| string      | No       | —          | visual help, not a replacement for `<label>` |

**Accessibility:**
- Use `<label for="...">` linked to all inputs
- Use `aria-describedby` for hints
- `aria-required` and error roles for validation

---

## Migration Example

### Deprecated: Old Button API

**Old:**
```jsx
<Button primary size="large" onClick={save} />
```
**New:**
```jsx
<Button variant="primary" size="lg" onClick={save} />
```

- See CHANGELOG.md for removal timeline
- Use a migration flag if supporting both APIs for transition

---

## Pattern for All Components
1. Create a file in Standards/ for the component (e.g., `Standards/Button.md`)
2. Document:
   - Visual spec (with tokens)
   - Tailwind/CSS usage
   - Full API table
   - Accessibility & ARIA details
   - Edge cases/responsiveness
   - Code migration patterns
3. Link in `DEVELOPER_HANDOFF.md` and Standards/README.md

---

## FAQ
- **Where do I find available tokens?** — See DESIGN.md
- **What if I need a variant not listed?** — Propose via GitHub Issue or add as Draft in Standards/
- **What if a token is missing in code?** — Open issue; code and Figma must match before promotion
- **How do I request breaking change?** — File RFC in Standards/, notify design system team

---

## See Also
- Accessibility.md (accessibility patterns)
- Maturity_Model.md (promotion checklist)
- QA_Checklist.md (testing before release)
- CHANGELOG.md (API migration/deprecation)
- CONTRIBUTING.md (general principles)
