# 6 · Governance & shipping

## Ownership

- **Standards owner:** your design system lead (set in [`.github/CODEOWNERS`](../../../.github/CODEOWNERS))
- **Brand values:** [`BRANDBOOK.md`](../../../BRANDBOOK.md)
- **Repo SSOT:** `DESIGN.md` at repo root or `docs/design.md`
- **Approved deviations:** `docs/design-exceptions.md`

## Sources of truth

1. **BRANDBOOK.md** — company brand identity
2. **Hub + Standards** — binding UI/UX rules
3. **Code (`globals.css`)** — what ships in production
4. **Figma library** — visual proof and component anatomy

If the hub and code disagree, **follow the code for implementation** and update the hub in the same PR.

## Shipping checklist

UI is ready to merge when:

- [ ] New project checklist completed ([1 · Scope & principles](../Standards/1%20%C2%B7%20Scope%20&%20principles%203454544eeb42810c89b3d3e4ef563c43.md))
- [ ] Components use documented variants (or logged exception)
- [ ] Token-only styling — no orphan hex
- [ ] Loading, empty, error, and success states covered
- [ ] Keyboard, focus, and semantics verified ([5 · Components & patterns](../Standards/5%20%C2%B7%20Components%20&%20patterns%203454544eeb4281479040ce5bd99406c7.md))
- [ ] Copy matches voice defined in BRANDBOOK.md
- [ ] Figma frame linked on the work item (or N/A with reason)
- [ ] Exceptions logged in `docs/design-exceptions.md` when deviating

## Figma integration

- Keep **one** team-owned Figma library URL current
- Library components map to ShadCN + Tailwind tokens in `globals.css`
- Prefer published components over detached copies

## External references (non-binding)

Material Design and Nielsen Norman Group inform baseline sizing and interaction patterns. They never override your brand tokens.
