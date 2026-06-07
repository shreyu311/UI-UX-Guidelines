# Woodside — UI/UX Compliance

**Compliance Score:** 57/60 (95%) · **Ship Date:** Mar 3, 2026 (demo completed) · **Overall:** 🟡 Partial

**Owner:** @Shreyas Shirke · **Reviewer:** Jorge Domenzain

---

## Phase 1 · Audit Findings

- What Exists ✅
    - Comprehensive UI/UX execution package (authored by Vraj)
    - UX North Star: "Staff can triage and update cases in under 60 seconds"
    - 3 primary users (Agent, Supervisor, Admin)
    - Locked conventions (case number format, 8-status model, KIPS categories, SLA timers)
    - Screen-by-screen spec (Login, My Cases, All Open, Due Soon, Case Detail, Manual Entry, Reporting)
    - FE ↔ BE contract checklist with API endpoints
    - Full design system from Woodside Brand Guide
    - 56 tasks with owners, dates, and per-task AC
    - 4 QA stages fully populated
    - Dual temporality SLA system
    - 8-step case workflow aligned to CGM protocol
    - Progressive permissions for 9 roles
    - Post-demo roadmap through Apr 27
- Critical Gaps ❌ / ⚠️
    - ⚠️ **No visual wireframes** — Lo-fi layout specs complete (Phase 3, Mar 25) but visual design tool exports (Figma/etc.) still pending
    - ✅ **Empty / Loading / Error states** — All 3 screens spec'd with Loading/Empty/Error/Success states + Spanish copy (Phase 4, Mar 25)
    - ✅ **Accessibility** — WCAG 2.1 AA declared + per-screen a11y checklists (Phase 5, Mar 25)
    - ⚠️ **Localization (Spanish)** — Spanish-first stated but no i18n string table
    - ⚠️ **7 open UI/UX questions** — All still marked Open, several past-due
    - 🔴 **Case state implementation gap** — Current system uses 3 states vs Masterplan's 8-step workflow
    - ❌ **Satisfaction survey UI** — Spec exists, no UI design
    - ❌ **Risk matrix classification UI** — Defined in Masterplan, no component designed
    - ❌ **Confidentiality toggle** — Required by IFC, no UI component
    - ✅ **Broken Mermaid diagrams** — Fixed Mar 25 (syntax errors resolved in Frontend Design Guidelines)
    - ⚠️ **10 pending client decisions** — Must validate before next phase

---

## Phase 2 · Current State Assessment

| **Dimension** | **Status** | **Evidence** |
| --- | --- | --- |
| Validated User Journeys | ✅ | 3 users defined (Agent, Supervisor, Admin). UX North Star set.  Mermaid workflow diagrams fixed (Mar 25). |
| Wireframes / Prototypes | ⚠️ | Lo-fi layout specs complete for 3 primary screens (Dashboard, Case Detail, Manual Entry) with pixel dimensions, responsive breakpoints (Desktop/Tablet/Mobile), and component architecture. See Phase 3. Visual design tool exports still pending. |
| Design System | ✅ | Full design system from Woodside Brand Guide (colors, typography, components, traffic lights). |
| Interaction States | ✅ | All 3 screens spec'd (Dashboard, Case Detail, Manual Entry) with Loading/Empty/Error/Success states and full Spanish copy. See Phase 4. |
| Accessibility | ✅ | WCAG 2.1 AA declared. Per-screen a11y checklists created for all 3 screens (Dashboard, Case Detail, Manual Entry). Lighthouse audit pending. See Phase 5. |
| Info Architecture | ✅ | 8-step CGM workflow, 6 KIPS categories, dual SLA system, progressive permissions for 9 roles all documented. |
| Dev Handoff | ⚠️ | 56 tasks with owners and dates. FE↔BE contract checklist exists. 7 open UI/UX questions still unresolved. |

---

## Phase 3 · Lo-Fi Wireframes (Top 3 Screens)

**Naming convention:** `Woodside-WF-[ScreenName]-v[X.X]`

| **Screen** | **What to Wireframe** | **Key Elements** | **Responsive Notes** |
| --- | --- | --- | --- |
| 1. Dashboard (My Cases / All Open) | Case list with SLA countdown timers, KIPS category badges (6 colors + text labels), status filters, due soon/overdue indicators | Dual SLA display (urgency + protocol stage), case number format (REQ-YYYY-####), traffic light indicators with text | Mobile-first (field staff). Case cards stack vertically on mobile. SLA timers remain visible. |
| 2. Case Detail | Full case view with 8-step workflow status bar, case metadata, timeline/history, attachments, stakeholder info, risk matrix badge | Workflow status showing all 8 CGM states (Recepción → Archivado), required fields per stage transition, confidentiality toggle, satisfaction survey (at Cierre stage) | Workflow bar collapses to dropdown on mobile. Timeline scrolls vertically. |
| 3. Manual Entry Form | New case creation form with required fields, KIPS category selector, urgency/priority picker, complainant info (with confidentiality toggle), file attachments | Progressive disclosure based on user role (Agent vs Supervisor vs Admin), validation messages in Spanish, risk matrix selector (probabilidad × impacto) | Form fields stack single-column on mobile. Touch targets ≥44×44px. |

### Woodside-WF-Dashboard-v1.0

**Desktop (1440px):**

- **Top Bar (56px):** Woodside logo (left) · Current user + role badge (Agent/Supervisor/Admin) · Language toggle ES/EN · Notification bell · Logout
- **KPI Strip (1×4, gap 16px):** Each card 200×90px — label (12px, secondary), value (28px bold), delta arrow. Cards: Mis Casos Abiertos: 14 ↑3 | Vencidos: 2 ↓1 | Promedio SLA: 4.2 días | Casos Cerrados (Mes): 38 ↑12
- **Filter Bar (48px):** Status dropdown (8-step: Recepción → Archivado) · KIPS category multi-select (6 categories with color dots) · Date range · SLA urgency (Crítico/Urgente/Normal/Bajo) · Search by case # or keyword · "Limpiar Filtros" link
- **Case List (full-width table, mt 16px):** Columns: Caso # (REQ-2026-####) | Estado (badge) | Categoría KIPS (color + text badge) | Descripción (truncated 80ch) | SLA (countdown timer with traffic light) | Prioridad | Responsable | Última Actualización. Sort on all columns. Pagination 20/page.
- **Traffic Light SLA Display:** Each case row shows dual timer — Urgencia (clock icon + days remaining, traffic light color) and Etapa Protocolo (step X of 8 + days in stage). Critical/overdue rows get `red_bg` highlight.
- **Floating Action Button (bottom-right):** "+Nuevo Caso" — opens Manual Entry form

**Tablet (1024px):** KPI strip → 2×2 grid. Filter bar → collapsible drawer ("Filtros" button). Case list → card view (case #, status badge, SLA timer, KIPS badge per card). FAB remains.

**Mobile (375px):** KPI strip → horizontal scroll. Case cards stack vertically. Touch targets ≥44×44px. Swipe right on card → quick status update.

### Woodside-WF-CaseDetail-v1.0

**Desktop (1440px):**

- **Breadcrumb (32px):** Mis Casos > REQ-2026-0042
- **Workflow Status Bar (64px, full-width):** 8-step horizontal stepper — Recepción → Registro → Evaluación → Investigación → Respuesta → Seguimiento → Cierre → Archivado. Current step highlighted (Woodside primary blue). Completed steps: green check. Future steps: gray. Each step clickable (if permissions allow transition).
- **Case Header (120px):** Case # (24px bold) | Status badge | KIPS category badge | Created date | SLA dual timer (urgency + protocol stage) | Confidentiality toggle (🔒 if IFC-flagged) | Priority badge
- **Content (65/35 split, gap 24px):**
    - Left (65%): Case description (full text) · Timeline/history (chronological entries: status changes, notes, attachments, each with timestamp + user) · Attachments list (file name, type icon, size, download link)
    - Right (35%): Stakeholder info card (complainant name — redacted if confidential, contact, location) · Risk matrix badge (probabilidad × impacto = nivel, e.g., Alta × Alto = Crítico) · Assigned team (owner + collaborators with role badges) · Related cases list
- **Action Bar (bottom, sticky 56px):** "Avanzar Estado" primary button (next workflow step) · "Agregar Nota" · "Adjuntar Archivo" · "Escalar" (supervisor+ only) · "Satisfaction Survey" button (visible only at Cierre stage)

**Tablet (1024px):** Content → single column (left above right). Workflow bar → scrollable horizontal or dropdown. Action bar remains sticky.

### Woodside-WF-ManualEntry-v1.0

**Desktop (1440px):**

- **Form Header (64px):** "Nuevo Caso de Queja" · Required fields marked with red asterisk
- **Progressive Sections (single column, max-width 720px, centered):**
    - **Section 1 — Información del Reclamante:** Nombre completo* · Teléfono · Email · Ubicación (address + map pin) · Relación con proyecto (dropdown) · Confidencialidad toggle ("Marcar como confidencial — IFC requerido")
    - **Section 2 — Detalle del Caso:** Categoría KIPS* (6-option radio with color indicators) · Descripción* (textarea, min 50 chars) · Fecha del incidente* · Ubicación del incidente
    - **Section 3 — Evaluación Inicial** (Supervisor/Admin only — progressive disclosure): Urgencia* (Crítico/Urgente/Normal/Bajo radio) · Matriz de Riesgo: Probabilidad (Baja/Media/Alta) × Impacto (Bajo/Medio/Alto) = auto-calculated severity badge · Asignar a* (team member dropdown)
    - **Section 4 — Archivos:** Drag-and-drop zone + "Seleccionar Archivos" button. Supported: PDF, JPG, PNG, DOCX. Max 10MB per file.
- **Form Actions (sticky bottom bar):** "Crear Caso" primary button · "Guardar Borrador" secondary · "Cancelar" text link
- **Validation:** Inline errors below each field in Spanish ("Este campo es obligatorio"). Form-level summary at top on submit attempt.

**Tablet/Mobile:** All sections stack. Touch targets ≥44×44px. File upload via camera capture option on mobile. Keyboard optimized per field type.

- [x]  Wireframe spec created — `Woodside-WF-Dashboard-v1.0`
- [x]  Wireframe spec created — `Woodside-WF-CaseDetail-v1.0`
- [x]  Wireframe spec created — `Woodside-WF-ManualEntry-v1.0`
- [ ]  Visual wireframes linked in project repository (design tool export pending)

---

## Phase 4 · Interaction States — Reference Screen: Dashboard (My Cases)

| **State** | **Visual Pattern** | **Copy / Behavior (Spanish)** |
| --- | --- | --- |
| **Loading** | Skeleton case cards (shimmer layout matching case card structure: case number, status badge, SLA timer, KIPS badge) + skeleton KPI row | No text during skeleton. SLA timers show "--:--:--" placeholder. |
| **Empty** | Illustration of empty inbox + descriptive copy + primary CTA | "No hay casos asignados en este momento. Puede crear un nuevo caso o ajustar los filtros de búsqueda." CTA: "Crear Nuevo Caso" |
| **Error** | Alert banner with error icon + human-readable message + retry. SLA API failure shows specific degraded state on timer area. | "No se pudieron cargar los casos. Verifique su conexión e intente nuevamente." Botón: "Reintentar" · SLA fallback: "Temporizador no disponible" |
| **Success** | Confirmation toast (top-right) for case creation, status update, or assignment change | "Caso REQ-2026-0042 creado exitosamente." or "Estado actualizado a Evaluación." |
- [x]  Loading state spec'd — skeleton case cards + SLA "--:--:--" placeholders
- [x]  Empty state spec'd — "No hay casos asignados" + Crear Nuevo Caso CTA
- [x]  Error state spec'd — Spanish error banner + SLA fallback text
- [x]  Success state spec'd — Spanish confirmation toasts
- [ ]  All copy stored in i18n string table (Spanish primary — pending extraction)

### Interaction States: Case Detail

| **State** | **Visual Pattern** | **Copy / Behavior (Spanish)** |
| --- | --- | --- |
| **Loading** | Skeleton workflow bar (8 gray circles) + skeleton header + skeleton timeline entries (3 shimmer rows) + skeleton stakeholder card | SLA timers show "--:--" placeholder. Workflow bar non-interactive until loaded. |
| **Empty** | Timeline section shows empty state with illustration + CTA | "No hay actividad registrada para este caso. Agregue una nota para comenzar." CTA: "Agregar Nota" |
| **Error** | Alert banner at top. If timeline fails to load: inline error in timeline area with retry. Workflow bar shows last-known state with stale indicator. | "No se pudo cargar el detalle del caso. Intente nuevamente." Botón: "Reintentar" · Timeline: "Error al cargar historial." |
| **Success** | Toast for status transitions, note additions, file uploads. Workflow bar animates step transition (300ms ease). | "Estado actualizado a Investigación." · "Nota agregada exitosamente." · "Archivo adjuntado — 2.4 MB." |

### Interaction States: Manual Entry Form

| **State** | **Visual Pattern** | **Copy / Behavior (Spanish)** |
| --- | --- | --- |
| **Loading** | Form shell visible, dropdowns show spinner while fetching options (team members, KIPS categories from API) | "Cargando opciones..." in dropdown placeholders. Submit button disabled until form interactive. |
| **Empty** | Default form state — all fields blank with placeholder text in Spanish | Placeholders: "Nombre completo del reclamante" · "Describa el incidente con detalle (mínimo 50 caracteres)" · "Seleccione categoría KIPS" |
| **Error** | Inline validation: red border + error text below field. Form-level: red banner at top listing all errors. File upload: per-file error badge. | Field: "Este campo es obligatorio" · "La descripción debe tener al menos 50 caracteres" · Form: "Corrija los errores antes de enviar (3 campos)" · File: "Archivo excede 10MB — seleccione otro" |
| **Success** | Full-page confirmation with case number + summary + next steps. Confetti animation optional. | "Caso REQ-2026-0043 creado exitosamente. El caso ha sido asignado a [Nombre] y se encuentra en etapa Recepción." CTA: "Ver Caso" · "Crear Otro" |

---

## Phase 5 · Accessibility Declaration

**Target:** WCAG 2.1 AA

**Project-specific requirements:**

- SLA countdown timers must have screen reader announcements (ARIA live region for urgent/overdue transitions)
- KIPS category badges use 6 colors — each **must** include text label (Ambiental, Social, Laboral, Seguridad, Gobernanza, Infraestructura)
- Traffic light indicators (Woodside brand) need text equivalents for all 3 states
- Case workflow 8-step status bar needs keyboard navigation between steps
- Form validation messages must be in Spanish and associated with form fields via `aria-describedby`
- Touch targets critical for field staff on mobile — validate all interactive elements ≥ 44×44px
- [x]  **WCAG 2.1 AA declared** in project card
- [x]  **Per-screen accessibility checklists created** (see below)
- [ ]  Lighthouse audit run (target ≥ 90) — run after visual wireframes are built

### Dashboard — A11y Checklist *(Dev status checked Mar 25)*

- [ ]  SLA countdown timers use `aria-live="polite"` for urgency transitions (Normal → Urgente → Crítico) — ⚠️ Visual SLA countdown pills implemented (Lochan, PR #101 Mar 5) but `aria-live` attribute not yet added. **Needs FE ticket.**
- [ ]  KIPS category badges use color + text label ("Ambiental" not just green dot) — ⚠️ KIPS 6-type badges implemented (Lochan, PR #101 Mar 5) + Design System QA'd (TASK-MP-08-FE). Visual badges exist; **verify text labels render alongside color** (not just colored dots).
- [ ]  Traffic light indicators use color + text ("Crítico: 2 días restantes" not just red) — ⚠️ SLA countdown pills show color; **verify text equivalents** ("Crítico: X días restantes") are displayed, not color-only.
- [ ]  Case list table uses `role="table"` with `aria-sort` on sortable column headers — ❌ No evidence of semantic table roles or `aria-sort`. **Needs FE ticket.**
- [ ]  Filter dropdowns keyboard-accessible with `aria-expanded` state — ❌ No evidence. **Needs FE ticket.**
- [ ]  FAB (Nuevo Caso) has `aria-label="Crear nuevo caso de queja"` — ❌ No evidence. **Needs FE ticket.**
- [ ]  Pagination controls: `aria-label="Navegación de páginas"` with current page announced — ❌ No evidence. **Needs FE ticket.**
- [ ]  Case cards on mobile have touch targets ≥44×44px — ⚠️ Mobile-responsive card layout implemented (Israel, Feb 26) with touch usability improvements. **Validate 44×44px threshold** in Lighthouse/manual audit.

### Case Detail — A11y Checklist

- [ ]  Workflow status bar uses `role="progressbar"` or `role="list"` with `aria-current="step"` on active step
- [ ]  Confidentiality toggle uses `role="switch"` with `aria-checked` and `aria-label="Marcar como confidencial"`
- [ ]  Risk matrix badge has text alternative ("Riesgo: Alta probabilidad × Alto impacto = Crítico")
- [ ]  Timeline entries are keyboard-navigable with visible focus indicators
- [ ]  Action bar buttons have descriptive `aria-label` ("Avanzar estado a Evaluación")
- [ ]  Attachments: download links announce file type and size ("Descargar informe.pdf, 2.4 MB")
- [ ]  Satisfaction survey (Cierre stage) form fields use `aria-describedby` for instructions

### Manual Entry — A11y Checklist

- [ ]  All required fields marked with `aria-required="true"` + visual asterisk
- [ ]  Inline validation errors linked via `aria-describedby` on their field
- [ ]  Form-level error summary uses `role="alert"` for immediate screen reader announcement
- [ ]  KIPS radio group uses `role="radiogroup"` with `aria-label="Categoría KIPS"`
- [ ]  Risk matrix auto-calculation announced via `aria-live="polite"` ("Nivel de riesgo: Crítico")
- [ ]  File upload zone has button fallback + `aria-label="Adjuntar archivos, formatos permitidos: PDF, JPG, PNG, DOCX"`
- [ ]  Progressive disclosure sections use `aria-expanded` on trigger and `aria-hidden` on collapsed content

---

## Phase 6 · Design Token Reference Sheet

<aside>
📐

**Brand alignment:** Woodside client brand guide tokens (not aosenuma internal)

</aside>

| **Category** | **Token** | **Value** | **Usage** |
| --- | --- | --- | --- |
| KIPS — Ambiental | `--color-kips-ambiental` | `#16A34A` (green-600) · 4.5:1 on white | Environmental category badges and filters |
| KIPS — Social | `--color-kips-social` | `#2563EB` (blue-600) · 4.6:1 on white | Social category badges and filters |
| KIPS — Laboral | `--color-kips-laboral` | `#EA580C` (orange-600) · 3.4:1 on white — pair with text label | Labor category badges and filters |
| KIPS — Seguridad | `--color-kips-seguridad` | `#DC2626` (red-600) · 4.6:1 on white | Safety category badges and filters |
| KIPS — Gobernanza | `--color-kips-gobernanza` | `#9333EA` (purple-600) · 4.6:1 on white | Governance category badges and filters |
| KIPS — Infraestructura | `--color-kips-infraestructura` | `#0D9488` (teal-600) · 4.5:1 on white | Infrastructure category badges and filters |
| Traffic — Crítico | `--color-traffic-critical` | `#DC2626` (red-600) · always paired with "Crítico" text | SLA overdue / critical urgency |
| Traffic — Urgente | `--color-traffic-urgent` | `#EA580C` (orange-600) · paired with "Urgente" text | SLA approaching deadline |
| Traffic — Normal | `--color-traffic-normal` | `#CA8A04` (yellow-600) · paired with "Normal" text | SLA on track |
| Traffic — Bajo | `--color-traffic-low` | `#16A34A` (green-600) · paired with "Bajo" text | SLA comfortable / low urgency |
| Background — Card | `--color-bg-card` | `#FFFFFF` (white) · `--shadow-sm` elevation | Case cards, KPI cards, stakeholder info panel |
| Background — Page | `--color-bg-page` | `#F1F5F9` (slate-100) | Dashboard background |
| Primary — Woodside Blue | `--color-primary` | `#1E3A5F` (Woodside brand navy) · 8.5:1 on white | Headers, active workflow step, primary CTAs |
| Accent | `--color-accent` | `#2563EB` (blue-600) | Links, secondary actions, focus rings |
| Border | `--color-border` | `#CBD5E1` (slate-300) | Card borders, table dividers, form field borders |
| Text — Primary | `--color-text-primary` | `#0F172A` (slate-900) | Headings, case data, form labels |
| Text — Secondary | `--color-text-secondary` | `#64748B` (slate-500) | Timestamps, descriptions, helper text |
| Typography — Heading | `font-heading` | Woodside brand font (per Brand Guide) | Page titles, section headers, case numbers |
| Typography — Body | `font-body` | Inter | Table data, form fields, timeline entries |
| Typography — Data | `font-data` | Barlow | KPI values, SLA countdown timers, dates |
| Spacing | `--space-*` | 4px / 8px / 12px / 16px / 24px / 32px / 48px | Component padding, card gaps, section margins |
| Components | shadcn/ui + custom | Card, Table, Badge, Form, Select, RadioGroup, Dialog, Sheet, Toast, Progress | Customized per Woodside Brand Guide palette |
- [x]  Design Token Reference Sheet created (KIPS colors, traffic lights, brand palette with hex values)
- [x]  Linked from project card

---

## Phase 7 · UI/UX Reporting Status

| **Field** | **Current Value** |
| --- | --- |
| Prototype Status | **In Progress** — layout specs complete, visual wireframes pending |
| Screens Completed | 3 of 3 (layout specs) · 0 of 3 (visual wireframes) |
| Screens Remaining | 3 visual wireframes (design tool export) |
| Interaction States Coverage | **100%** — all 3 screens spec'd (Dashboard, Case Detail, Manual Entry) with Loading/Empty/Error/Success |
| Accessibility Compliance | **WCAG 2.1 AA declared** · Per-screen a11y checklists created · Lighthouse audit pending |
| Open UI/UX Decisions | 7 UI/UX questions + 10 client decisions — all assigned with owners + due dates (see Phase 8) |
| Stakeholder Sign-off | Pending — target Jorge review by Mar 20 |
- [x]  UI/UX status section added to RAD log (template + current values populated above)
- [x]  All open decisions logged with owner + due date (see Phase 8 below)

---

## Phase 8 · Final Compliance Check

| **Compliance Item** | **Status** |
| --- | --- |
| Lo-fi wireframes for top 3 screens — linked in repo | ✅ Layout specs complete — visual wireframes pending design tool export |
| Interaction states documented for ≥1 primary screen | ✅ All 3 screens covered (Dashboard, Case Detail, Manual Entry) |
| WCAG 2.1 AA declared in project card | ✅ |
| Design Token Reference Sheet created and linked | ✅ KIPS colors, traffic lights, brand palette with hex values |
| UI/UX status section in RAD log | ✅ Template populated with current values |
| Open UI/UX decisions logged with owners + due dates | ✅ 7 UI/UX + 10 client decisions — all assigned |
| Hi-fi prototype naming convention established | ✅ `Woodside-HF-[ScreenName]-v[X.X]` |

### Open Decisions — UI/UX Questions

| **Decision** | **Owner** | **Due** | **Status** |
| --- | --- | --- | --- |
| W1 — Case state implementation (3 current vs 8-step CGM workflow) | Shreyas + Dev | Mar 19 | **Rec: Implement full 8-step** — CGM protocol compliance required |
| W2 — Spanish i18n string table format and extraction workflow | Shreyas | Mar 19 | **Rec: JSON key-value** — standard React i18n compatible |
| W3 — Satisfaction survey UI component and trigger point | Vraj | Mar 19 | **Rec: Modal at Cierre stage** — 5-question NPS-style |
| W4 — Risk matrix classification component design | Shreyas | Mar 19 | **Rec: 3×3 grid picker** — probabilidad × impacto with auto-severity |
| W5 — Confidentiality toggle behavior and data masking scope | Vraj | Mar 19 | **Rec: Toggle masks complainant PII** — IFC minimum compliance |
| W6 — Broken Mermaid diagrams in Frontend Design Guidelines | Shreyas | Mar 18 | ✅ **RESOLVED Mar 25** — Split monolithic block into 7 separate diagrams, added stateDiagram-v2, fixed note syntax, fixed classDiagram multiplicities |
| W7 — SLA dual-timer display format and countdown behavior | Shreyas | Mar 19 | **Rec: Urgency (days) + Protocol stage (step X/8)** — per wireframe spec |

### Open Decisions — Client Decisions

| **Decision** | **Owner** | **Due** | **Status** |
| --- | --- | --- | --- |
| 10 pending client decisions (Part E validation items) | Shreyas (PM) | Mar 19 | **Open** — email sent to client PM. If no response by Mar 19, assume defaults per spec and log as gate exception. |