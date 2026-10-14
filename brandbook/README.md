# Brand book (Layer B)

The brand book holds everything specific to one brand: name, audience, voice, colors, typography, logo, shape, density, and brand-specific constraints. The core rules in [`../DESIGN.md`](../DESIGN.md) stay the same for every brand; the brand book decides the values.

```
brandbook/
├── README.md               This guide
├── brandbook.template.md   Blank template (keep it unchanged)
├── brandbook.md            Your brand book (you create it from the template)
└── assets/                 Your logo and other brand files (optional)
```

`brandbook.md` doesn't exist in this repository; each user creates their own.

---

## Set up your brand book

1. Copy the template:

   ```bash
   cp brandbook/brandbook.template.md brandbook/brandbook.md
   ```

   On Windows PowerShell: `Copy-Item brandbook/brandbook.template.md brandbook/brandbook.md`

2. Fill in what you know. Leave any `[PLACEHOLDER]` you haven't decided yet; the framework uses a neutral fallback for it.
3. Check every color pair you entered for contrast (see below) and note the results in the template's contrast table.
4. Add logo files to `assets/` if you have them and are allowed to share them.
5. Commit `brandbook/brandbook.md` in your own copy or fork of the framework.

You never need to edit `DESIGN.md` to apply a brand.

---

## How brand values are applied

Precedence, as defined in [`DESIGN.md` §1](../DESIGN.md#1-how-the-core-rules-and-the-brand-book-work-together):

1. **MUST rules** in `DESIGN.md` always apply.
2. **Brand book values** set colors, fonts, logo, shape, density, and voice.
3. **SHOULD defaults** in `DESIGN.md` apply where the brand book is silent.
4. **Neutral fallbacks** in `DESIGN.md` §3.4–3.5 fill any value the brand book doesn't provide.

What that means in practice:

| Situation | What happens |
| --- | --- |
| A field is filled in | The value is mapped to the token named in the template's "Maps to" column. |
| A field still has a `[PLACEHOLDER]` | The neutral fallback is used, and the gap is reported (BRD-4). |
| No `brandbook.md` exists | Everything uses fallbacks; output is clearly neutral, not a made-up brand (BRD-2). |
| A brand value conflicts with a SHOULD default | The brand value wins. Record the reason in the template's "Constraints and exceptions" section. |
| A brand value would break a MUST rule | See the next section. |

---

## When a brand value breaks a MUST rule

The most common case is a brand color that is too light to pass contrast as text (CLR-1). The rule stays; the brand value is used only in roles where it passes:

1. **Measure it.** Use a contrast checker (for example, the [WebAIM contrast checker](https://webaim.org/resources/contrastchecker/)) against the surfaces it will sit on.
2. **Keep the color, change the role.** A color that fails as text on white can often still be a background fill with dark text on it, or decoration that carries no meaning.
3. **Add an accessible shade if needed.** Define a darker or lighter shade in your brand palette for text and controls, and map that shade to the semantic token (for example, `color.action.primary`). Keep the original as a decorative brand color.
4. **Write it down.** Record the restriction in "Constraints and exceptions" so every person and tool applies it the same way.

The worked example in [`../examples/README.md`](../examples/README.md) shows this with a fictional brand.

---

## Fallbacks are not a brand

The fallback palette is grays plus one conventional blue, chosen only because it meets contrast requirements. If the output of a prototype looks generic, that's a signal to fill in more of the brand book. It's not a style to adopt.

---

## Several brands or products

Keep one file per brand, for example `brandbook/brand-a.md` and `brandbook/brand-b.md`, and state which one is active:

- for people: at the top of the prototype brief;
- for AI assistants: in the prompt ("Use `brandbook/brand-a.md` as the brand book").

All brands share the same `DESIGN.md`.

---

## Completeness checklist

- [ ] Brand name, product context, and audience are filled in
- [ ] Primary action color and text colors are set, with contrast results recorded
- [ ] Status colors are set, or you've decided to use the fallbacks
- [ ] Fonts are chosen, with fallback stacks, and you're licensed to use them
- [ ] Dark mode is marked as supported or not supported (and, if supported, dark values are given)
- [ ] Logo files and usage rules are in place, or marked "none yet"
- [ ] Voice and tone guidance includes at least one do and one don't
- [ ] Constraints and exceptions are listed
