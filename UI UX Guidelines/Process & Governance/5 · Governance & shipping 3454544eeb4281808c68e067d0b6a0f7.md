# 5 · Governance & shipping

## Ownership

- **Standards owner:** Shreyas Shirke
- **Repo SSOT:** `design.md` in `docs/` or repo root
- **Approved deviations:** `docs/design-exceptions.md`

## Sources of truth

- **Engineering merge gate:** the Markdown UI specification checked into Git under **docs** (and optionally at the repository root—see **Ownership** for the exact filename). If a PR conflicts with that file, update it first or log an approved exception in the exceptions Markdown next to it.
- **Design narrative:** this Notion hub is the human-friendly reference (examples, Figma links, tables). If Notion and the Git spec disagree, **follow the Git spec for code** until both are updated together.
- **Workshop snapshots:** PDF or HTML exports (for example the stakeholder **Components Reference** booklet tied to v1.0 of the Git spec) can lag. Refresh them after substantive changes. **Shreyas Shirke** (or delegated design ops) owns export cadence.

### Export checklist (design ops)

- [ ]  After substantive Notion edits, mirror the same rules into the Git-tracked Markdown spec under **docs** (or the root copy) in the same release window when engineering relies on the file.
- [ ]  Regenerate the **Components Reference** PDF (or print-to-PDF from the HTML reference) so workshop handouts match the hub.
- [ ]  Confirm the **embedded gallery** callouts in **Brand, layout & tokens** contain current Figma links or PNGs.
- [ ]  Confirm the **canonical Figma library URL** is easy to find (tickets, **2 · Brand**, and **Figma integration (workflow)** below) and that **1 · Scope** → *New project / new frame checklist (Apr 14 baseline)* stays the single checklist source.

## How we extend these guidelines

1. **Categorize UI** (actions, forms, feedback, navigation, data display) and document anatomy, spacing, and states per pattern.
2. **Use NN/g + Material** only as **baseline** references for sizing, density, and interaction — **aosenuma tokens + ShadCN** stay authoritative in shipped UI.
3. **Show decisions on components** in the shared Figma library (color, motion, spacing, hierarchy) — not swatch-only slides.
4. **Call out density** differences (e.g. admin vs marketing) directly in Figma frames.

## Shipping checklist

UI is ready to merge when:

- [ ]  **New project / new frame (Apr 14 baseline)** — every item in [1 · Scope & principles](../Standards/1%20%C2%B7%20Scope%20&%20principles%203454544eeb42810c89b3d3e4ef563c43.md) → *New project / new frame checklist (Apr 14 baseline)* (canonical checklist; link only—do not duplicate the list here).
- [ ]  **ShadCN** components (or a **documented fork** — see **4 · Components & patterns**)
- [ ]  **Token-only** styling — no orphan hex in frames or code
- [ ]  **Loading · empty · error · success** covered
- [ ]  **Keyboard, focus, semantics** verified against **4 · Components & patterns**
- [ ]  **Copy** matches voice (**aosenuma** lowercase, warm, concise)
- [ ]  **Figma** library + frame linked on the work item (or **N/A** with reason)
- [ ]  **Exceptions** logged in `docs/design-exceptions.md` when deviating

## Figma integration (workflow)

- **Canonical library link:** keep **one** team-owned Figma library URL current. Surface it in **Export checklist** above, on tickets/PRs, and in **2 · Brand, layout & tokens** (Figma handoff). Designers and devs should never guess which file is authoritative.
- **Components ↔ code:** library components and variables map to **ShadCN + Tailwind** tokens in `globals.css`. Prefer published components over detached copies; name variants the same way Dev Mode will read them.
- **“Fix now” triage (when components error or won’t open):** treat as **publish / instance hygiene first**, then **permissions**, then **true UX defects**.
    1. **Publish hygiene:** unpublish/republish the component set; confirm no conflicting duplicate names in the file.
    2. **Detached instances / mixed libraries:** reset to library source or swap to the correct library; note the library key in the ticket.
    3. **Permissions / seat / org:** verify the viewer can access the **published** library (not only a duplicate draft).
    4. **Still broken:** capture a Loom + file version + frame URL; assign **design ops** for file repair vs **engineering** if the issue reproduces only after export or in code.
- **Deep file repair** (orphaned masters, corrupted variants) is **out of band** for this doc—log owner and link here once resolved.

## Meeting & audit references (Apr 14, 2026)

- **Meet transcript (Google Doc):** [Apr 14 UI/UX design system discussion](https://docs.google.com/document/d/1ER2jHTVNHb9ULXNh8pFqtHx157TP8tSjvq33KqIzaGU/edit)
- **Calendar:** use the **read-only** calendar invite for the recurring UI/UX design sync (same series as Apr 14, 2026). Paste the public **Calendar** or **Meet** link from Google Calendar into this bullet when available; until then, request the link from **design ops**.

## External references (non-binding)

**Material Design** and **Nielsen Norman Group** inform baseline sizing, spacing, and interaction patterns. Visual mood boards never override these guidelines.

- Superseded page splits (archive)
    
    Earlier Notion splits are kept only for history. Prefer the **five** child pages in this hub for day-to-day work.
    

[Archive — superseded 12-way split (2026-04-17)](5%20%C2%B7%20Governance%20&%20shipping/Archive%20%E2%80%94%20superseded%2012-way%20split%20(2026-04-17)%203454544eeb428102bd52cf241f65aeb4.md)