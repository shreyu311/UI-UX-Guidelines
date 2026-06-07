> **⚠ Pilot / product-specific DESIGN file (not organizational SSOT).**  
> This specification was used for an **experimental “Financial Editorial & Market Insight”** direction (palette intentionally diverges from the company hub).  
> **Default tokens for org tooling:** repo root [`DESIGN.md`](../../../DESIGN.md) and canonical hub [`UI UX guidelines`](../../../UI%20UX%20Guidelines/UI%20UX%20guidelines%2020be6c5f913d4f53ac0e76eb5e904eef.md). See [`Projects/README`](../README.md).

---

# Design System Specification: Financial Editorial & Market Insight

## 1. Overview & Creative North Star
### The Creative North Star: "The Fluid Analyst"
In the world of high-stakes finance, data is often treated as rigid and cold. This design system breaks that mold by embracing a "Fluid Analyst" philosophy. It merges the precision of market data with the organic "finding edges" metaphor inspired by the rhythmic wave patterns in our visual identity. 

The system moves away from the "Dashboard-in-a-Box" aesthetic. Instead, it utilizes **Editorial Asymmetry** and **Tonal Depth** to guide the eye. We prioritize breathing room over information density, using wide margins and overlapping elements to create a bespoke, premium experience. This isn't just a tool; it's a curated financial intelligence environment.

---

## 2. Colors
Our palette is rooted in deep sea tones and crisp seafoam accents, designed to convey authority and modern clarity.

### Color Tokens
- **Primary (Deep Navy/Teal):** `#00373b` (Primary) | `#005055` (Primary Container)
- **Secondary (Seafoam):** `#306576` (Secondary) | `#b3e8fb` (Secondary Container)
- **Neutral/Background:** `#f7fafa` (Surface) | `#ffffff` (Surface Lowest)
- **Accents:** `#0a3833` (Tertiary) | `#77d5dd` (Inverse Primary)

### The "No-Line" Rule
To maintain a high-end editorial feel, **1px solid borders are prohibited for sectioning.** Boundaries must be defined solely through background color shifts or tonal transitions. Use `surface_container_low` (`#f1f4f4`) against a `surface` (`#f7fafa`) background to create a distinct section without the "boxed-in" feeling of traditional grids.

### Surface Hierarchy & Nesting
Treat the UI as a series of physical, layered sheets. 
*   **Base:** `surface` (`#f7fafa`)
*   **Nesting Level 1:** Use `surface_container_low` (`#f1f4f4`) for large content blocks.
*   **Nesting Level 2 (The Inset):** Use `surface_container_highest` (`#e0e3e3`) for specific data widgets within a section.

### The "Glass & Gradient" Rule
For "Quick Picks" or Market Alerts, use **Glassmorphism**: 
*   **Surface:** `surface_container_lowest` (`#ffffff`) at 70% opacity.
*   **Effect:** `backdrop-filter: blur(12px)`.
*   **Gradients:** Main CTAs should use a subtle linear gradient from `primary` (`#00373b`) to `primary_container` (`#005055`) at 135 degrees to provide visual "soul" and depth.

---

## 3. Typography
We use a dual-typeface system to balance technical authority with editorial elegance.

*   **Display & Headlines (Manrope):** Chosen for its geometric precision and wide apertures. Use `display-lg` (3.5rem) for hero market stats to create an "impact" moment.
*   **Body & Labels (Inter):** The workhorse for data. Its high x-height ensures readability in dense market tables.

**Hierarchy as Identity:** 
*   **Headline-md (1.75rem):** Use for section titles, always paired with a `label-md` (0.75rem) "over-line" in `secondary` (`#306576`) to establish a sophisticated data hierarchy.

---

## 4. Elevation & Depth
In this system, "Elevation" is a measure of light and tone, not just shadows.

### The Layering Principle
Depth is achieved by "stacking" surface tiers. To make a card "pop," place a `surface_container_lowest` (`#ffffff`) card on top of a `surface_container` (`#ebeeee`) background. This creates a soft, natural lift.

### Ambient Shadows
For floating elements (Modals, Dropdowns), use **Ambient Shadows**:
*   **Blur:** 24px - 40px.
*   **Color:** `#181c1d` (on-surface) at 4% to 6% opacity.
*   **Style:** Avoid dark, heavy drops; the shadow should feel like a soft glow of "negative light."

### The "Ghost Border" Fallback
If contrast ratios or accessibility require a container edge, use a **Ghost Border**:
*   **Token:** `outline_variant` (`#c0c8cb`) at 15% opacity. This provides a "suggestion" of an edge without breaking the fluid aesthetic.

---

## 5. Components

### Cards & Market Data
*   **Style:** No borders. Use `roundedness-lg` (1rem).
*   **Spacing:** Use `spacing-6` (1.5rem) internal padding.
*   **Interaction:** On hover, shift background from `surface_lowest` to `surface_bright` and increase shadow opacity by 2%. Do not use "lift" animations; use tonal shifts.

### Buttons
*   **Primary:** Gradient of `primary` to `primary_container`. `roundedness-full`.
*   **Secondary:** Ghost style using the "Ghost Border" rule. Text in `primary`.
*   **Tertiary:** Text-only, using `label-md` in `secondary`.

### Input Fields
*   **Visuals:** Subtle `surface_container_high` fill. No bottom line.
*   **Active State:** Transitions to a 1px `primary` ghost border (20% opacity) and a very slight inner shadow.

### Signature Motifs (The "Edge" Pattern)
*   Integrate the wave-like line motifs from the reference image as **background watermarks** behind `headline-lg` elements.
*   The lines should use `outline_variant` at 10% opacity, appearing to "flow" through data containers, symbolizing the fluid nature of market trends.

---

## 6. Do's and Don'ts

### Do
*   **Do** use asymmetrical layouts (e.g., a 7-column main area and a 5-column sidebar) to create an editorial feel.
*   **Do** use vertical white space (`spacing-12` or `spacing-16`) to separate major narrative sections.
*   **Do** apply the wave pattern motif to the background of empty states or loading skeletons to maintain brand texture.

### Don't
*   **Don't** use 100% opaque black or grey for shadows. 
*   **Don't** use dividers (`<hr>`). Use a 24px gap or a background tonal shift (`surface` to `surface_container_low`) instead.
*   **Don't** cram data. If a table has more than 8 columns, move secondary data into an expandable "drawer" to preserve the "Clean & Professional" aesthetic.
*   **Don't** use "Default" blue links. Use `secondary` (`#306576`) with a medium-weight underline for inline links.