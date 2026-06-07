# Release review checklist

> **Former location:** Part IV — § 15.
> 

## PR / review checklist (quick compliance)

- [ ]  Uses ShadCN components (or fork documented)
- [ ]  Uses token-driven styling (no one-off colors)
- [ ]  Includes loading / empty / error / success states
- [ ]  Accessible interactions (keyboard + focus)
- [ ]  Copy tone matches brand (warm, concise, aosenuma lowercase)

### PR snippet (copy/paste into every UI PR)

**UI/UX Standard compliance (required)**

- `design.md` referenced: (link)
- Figma: canonical library + frame link (or N/A if no visual change): (links)
- Tokens used (no one-off colors): Yes/No
- ShadCN-first (fork documented if needed): Yes/No
- States included: Loading / Empty / Error / Success
- Accessibility: keyboard + focus + semantic structure verified
- Exceptions filed (if any): `docs/design-exceptions.md` (link)