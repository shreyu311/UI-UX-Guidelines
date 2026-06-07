# Changelog

**Purpose:** Document all design system changes, promotions, deprecations, and breaking changes in one place. Teams subscribe to this to stay informed.

**Update frequency:** Weekly (as changes are made) or at release boundaries (monthly recommended).

---

## [Unreleased]

### Added
- **Accessibility.md** — WCAG 2.1 AA compliance matrix, contrast pre-verification, keyboard navigation guide
- **Maturity_Model.md** — Component lifecycle: Draft → Stable → Optimized → Sunset
- **Developer_Handoff.md** — CSS/Tailwind code examples, component API specs, code migration patterns
- **QA_Checklist.md** — Component compliance testing guide, manual audit steps, automation tools
- **Performance.md** — CSS file size targets, image optimization, lazy-loading guidance
- **Maintenance.md** — Living documentation process, feedback loops, quarterly cadence

### Changed
- **CONTRIBUTING.md:** Added explicit step "If touching semantic tokens, update DESIGN.md in same PR"
- **README.md:** Added links to new governance docs (Accessibility, Maturity Model, Changelog)

### Deprecated
- `Breadcrumb` component → Replaced by `Pagination` (removal Aug 15, 2025)

### Fixed
- Button focus indicator now includes `outline-offset: 2px` (improved keyboard visibility)
- Modal: Added `focus-trap` utility to prevent focus escape

---

## [v2.0.0] — 2025-05-15

### Major Changes (Breaking)

#### ❌ Button component API redesigned
- **Old:** `<Button variant="primary" size="lg" />`
- **New:** `<Button level="primary" scale="lg" />`
- **Why:** Align terminology with design tokens (`level` = semantic role, `scale` = size)
- **Migration:** See DEVELOPER_HANDOFF.md "Button API migration"
- **Removal date:** Aug 15, 2025
- **Impact:** ⚠️ All teams using `<Button>` must update by deadline

#### ✅ Semantic tokens renamed for clarity
- **Old:** `color-primary`, `color-secondary`, `color-destructive`
- **New:** `color-cta-primary`, `color-cta-secondary`, `color-semantic-destructive`
- **Why:** Reduce naming collisions; make purpose explicit
- **Migration:** Updated in DESIGN.md and Figma
- **Tools:** ESLint rule `no-orphan-colors` enforces new tokens

### Added
- **Button: Outline variant** (new) — Outlined buttons for secondary actions
- **Form: Input with icon** — Icon slots (left/right) for input fields
- **Spacing tokens:** New `spacing-xs` (2px), `spacing-2xs` (1px) for micro-adjustments
- **Typography:** Added `font-weight-medium` (500) for labels
- **Accessibility audit:** All Stable components pass WCAG 2.1 AA ✅

### Changed
- **Modal: Overflow behavior** — Modal body now uses `overflow-y: auto` (was `overflow: hidden`)
- **Tooltip: Show delay** — Increased from 100ms to 200ms to reduce false positives
- **Color palette:** Updated `warning` from `#F59E0B` to `#EAB308` (improved contrast on light backgrounds)

### Deprecated
- `font-size-caption` → Use `label-sm` (announcement; removal Q3 2025)
- `Button` old API → Migrate to new API by Aug 15, 2025

### Fixed
- Dropdown menu: Fixed keyboard arrow navigation (was skipping disabled items)
- Checkbox: Fixed focus indicator on Windows high-contrast mode
- Link underline: Now respects `text-decoration-thickness` on all browsers
- Grid: Fixed 12-column layout on iPad (was collapsing to 1 column)

### Performance
- **Bundle size:** Design tokens CSS reduced by 22% (8.2kb → 6.4kb)
- **Figma:** Component auto-code generation now 40% faster

### Security
- Removed inline event handlers from HTML examples (all use `addEventListener` now)

---

## [v1.3.1] — 2025-04-20

### Fixed
- Accessibility: Form error messages now announce correctly with `aria-live="polite"`
- Accessibility: Dropdown menu now has proper ARIA roles (`role="menu"`, `role="menuitem"`)
- Performance: Reduced CSS file size by removing unused media queries

---

## [v1.3.0] — 2025-04-15

### Added
- **Accessibility.md:** WCAG 2.1 AA compliance matrix (contrast table, keyboard nav guide)
- **Dropdown component:** New `closeOnSelect` prop (default: true)
- **Color: Info semantic token:** `#3B82F6` for informational messages

### Changed
- **Modal: Backdrop click behavior** — Now respects `closeOnBackdropClick` prop (was always closeable)
- **Input: Error state styling** — Border now uses `color-semantic-destructive` (was hardcoded red)

### Deprecated
- Old contrast checker links in documentation (replaced by WebAIM + axe DevTools)

---

## [v1.2.0] — 2025-03-20

### Added
- **Button disabled state:** Proper contrast-compliant styling for disabled buttons
- **Typography guide:** Line-height recommendations for readability (1.5 for body, 1.2 for headings)
- **Component QA checklist:** Manual testing steps for all Stable components

### Fixed
- Checkbox: Fixed focus ring visibility on dark backgrounds
- Select: Fixed scrolling behavior in long option lists (was cutting off options)

---

## [v1.1.0] — 2025-02-28

### Added
- **Pagination component:** Promoted from Draft to Stable ✅
- **Maturity model:** Draft → Stable → Optimized → Sunset stages
- **Performance targets:** Bundle size limits per component

### Changed
- **Focus indicator:** All interactive elements now have consistent focus ring (`2px solid [YOUR_PRIMARY]`)

---

## [v1.0.0] — 2025-01-15 — Initial Release

### Added
- **Semantic color palette:** Primary teal, secondary sage, destructive red, success, warning, info
- **Layout grid:** 8pt grid system; spacing scale (4/8/16/24/32/48/64)
- **Components (Draft → Stable):**
  - Button (primary, secondary, ghost, destructive)
  - Input (text, email, password, number)
  - Checkbox
  - Radio button
  - Select dropdown
  - Modal
  - Tooltip
  - Dropdown menu
- **Typography:** Body, headline, display hierarchy with font sizes
- **Figma library:** Component auto-sync with GitHub code library
- **DESIGN.md:** Agent/Stitch projection for code generation

---

## Deprecation Timeline

| Component | Announced | Removal Date | Migration |
|-----------|-----------|--------------|-----------|
| `Breadcrumb` | May 2025 | Aug 15, 2025 | → Pagination |
| `Button` (old API) | May 2025 | Aug 15, 2025 | See DEVELOPER_HANDOFF.md |
| `font-size-caption` | May 2025 | Sep 1, 2025 | → `label-sm` |

---

## Version Numbering

This project uses [Semantic Versioning](https://semver.org/):

- **MAJOR** (v2.0.0): Breaking API changes, component removals
- **MINOR** (v1.3.0): New features, non-breaking additions
- **PATCH** (v1.3.1): Bug fixes, security patches, performance improvements

### Breaking Change Threshold

A change is "breaking" if:
- Component API changes (prop names, types, return values)
- Semantic token removed (no replacement)
- HTML structure changes (grid columns, heading levels)
- CSS class name changes (if using utility classes)

**Not breaking:**
- New token added (old one still works)
- New component variant (old variants unchanged)
- Visual refinement (no API change)
- Performance improvement (no API change)

---

## How to Update This File

1. **During development:** Add entries to `[Unreleased]` section
2. **At release:** Create new version heading with date (format: `[vX.Y.Z] — YYYY-MM-DD`)
3. **Notify teams:** Post in Slack #design-system channel with summary
4. **Tag Git commit:** `git tag v1.3.0` (matches section heading)

### Template

```markdown
## [vX.Y.Z] — YYYY-MM-DD

### Added
- Feature or component name

### Changed
- Behavior change or redesign

### Deprecated
- Component/token/API planned for removal

### Removed
- Component/token/API removal (only in major versions)

### Fixed
- Bug fix

### Security
- Security patch

### Performance
- Performance improvement
```

---

## Subscribing to Changes

- **RSS feed:** [GitHub releases](https://github.com/sashirke-ship-it/UI-UX-Guidelines/releases)
- **Email:** Watch GitHub repo (Settings → Notifications)
- **Slack:** Subscribe via workflow automation (ask @admin to set up)
- **Docs:** Link this file in your team's internal design system intake doc

---

## Questions?

- **"When do I update my code?"** → Check the removal date; plan migration before then
- **"Is this breaking change for me?"** → Search Changelog for your component name
- **"Can we stay on old API?"** → Only until removal date; no long-term support
