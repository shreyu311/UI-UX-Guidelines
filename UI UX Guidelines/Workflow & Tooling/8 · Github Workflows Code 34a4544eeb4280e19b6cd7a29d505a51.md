# 8 · Github Workflows Code

```yaml
name: design-drift

on:
  pull_request:
    paths:
      - "docs/design.md"
      - "app/globals.css"
      - "scripts/check-design-tokens.mjs"
      - ".github/workflows/design-drift.yml"
  workflow_dispatch:

jobs:
  check-design-token-drift:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: "20"

      - name: Run token drift check
        run: node scripts/check-design-tokens.mjs

਍
```

```css
:root {
  --background: 0 0% 100%;
  --foreground: 222.2 84% 4.9%;

  --primary: 186 64% 35%;
  --primary-hover: 191 60% 22%;
  --primary-foreground: 0 0% 100%;

  --success: 142 76% 37%;
  --success-bg: 138 76% 93%;
  --success-foreground: 142 72% 20%;

  --warning: 38 92% 50%;
  --warning-bg: 48 96% 89%;
  --warning-foreground: 25 95% 20%;

  --destructive: 0 72% 51%;
  --destructive-hover: 0 74% 42%;
  --destructive-bg: 0 86% 92%;
  --destructive-foreground: 0 0% 100%;

  --muted: 210 20% 96%;
  --muted-foreground: 220 9% 46%;
  --border: 220 13% 82%;
  --disabled-fill: 220 13% 82%;
  --disabled-text: 220 9% 64%;

  --info: 217 91% 60%;
  --info-bg: 214 100% 97%;
  --info-foreground: 217 70% 28%;

  --radius: 0.75rem;
  --ring: var(--primary);
}

਍
```

```markdown
# design.md

## Sync Header

Notion hub is canonical for narrative and visuals: [UI/UX guidelines](https://www.notion.so/aosenuma-ai/UI-UX-guidelines-20be6c5f913d4f53ac0e76eb5e904eef?source=copy_link).
This file is canonical for tokens and component APIs used in code.
If this file and implementation drift, log an exception in `docs/design-exceptions.md`.
Do not ship unlogged drift.

## Owner and Status

- Owner: Shreyas Shirke
- Status: v1 mirror from Apr 2026 hub export
- Stack target: Next.js App Router + Tailwind + ShadCN

## Token Contract (Non-Negotiable)

| Role | Tailwind intent | CSS variables | Hex | Use for | Never use for |
| --- | --- | --- | --- | --- | --- |
| Primary / Teal | `bg-primary text-primary-foreground` | `--primary`, `--primary-foreground`, `--ring` | `#208692` default, `#164F5B` hover | CTAs, links, focus rings, active states | Errors, failure states |
| Success / Green | `bg-success text-success-foreground` | `--success`, `--success-foreground`, `--success-bg` | `#16A34A` base, `#DCFCE7` bg | Confirmation, completed states, success toast | Warnings or errors |
| Warning / Amber | `bg-warning text-warning-foreground` | `--warning`, `--warning-foreground`, `--warning-bg` | `#F59E0B` base, `#FEF3C7` bg | Non-blocking risk, missing required info | Blocking errors |
| Destructive / Red | `bg-destructive text-destructive-foreground` | `--destructive`, `--destructive-foreground`, `--destructive-bg` | `#DC2626` base, `#B91C1C` hover, `#FEE2E2` bg | Blocking errors, irreversible danger | Marketing emphasis, success |
| Neutral / Gray | `bg-muted text-muted-foreground` | `--muted`, `--muted-foreground`, `--border` | `#6B7280`, `#D1D5DB`, `#F3F4F6` | Disabled, secondary text, borders, surface bg | Active interactive elements |
| Info / Calm Blue | `bg-info text-info-foreground` | `--info`, `--info-foreground`, `--info-bg` | `#3B82F6` base, `#EFF6FF` bg | Informational banners and notices | Errors or warnings |

## Source-of-Truth `globals.css` Excerpt

```css
:root {
  --background: 0 0% 100%;
  --foreground: 222.2 84% 4.9%;

  --primary: 186 64% 35%;              /* #208692 */
  --primary-hover: 191 60% 22%;        /* #164F5B */
  --primary-foreground: 0 0% 100%;

  --success: 142 76% 37%;              /* #16A34A */
  --success-bg: 138 76% 93%;           /* #DCFCE7 */
  --success-foreground: 142 72% 20%;

  --warning: 38 92% 50%;               /* #F59E0B */
  --warning-bg: 48 96% 89%;            /* #FEF3C7 */
  --warning-foreground: 25 95% 20%;

  --destructive: 0 72% 51%;            /* #DC2626 */
  --destructive-hover: 0 74% 42%;      /* #B91C1C */
  --destructive-bg: 0 86% 92%;         /* #FEE2E2 */
  --destructive-foreground: 0 0% 100%;

  --muted: 210 20% 96%;                /* #F3F4F6 */
  --muted-foreground: 220 9% 46%;      /* #6B7280 */
  --border: 220 13% 82%;               /* #D1D5DB */
  --disabled-fill: 220 13% 82%;        /* #D1D5DB */
  --disabled-text: 220 9% 64%;         /* #9CA3AF */

  --info: 217 91% 60%;                 /* #3B82F6 */
  --info-bg: 214 100% 97%;             /* #EFF6FF */
  --info-foreground: 217 70% 28%;

  --radius: 0.75rem;                   /* 12px */
  --ring: var(--primary);
}
```

## Gradient Token

- Approved gradient only: `linear-gradient(135deg, #164F5B 0%, #208692 100%)`.
- Token name: `--gradient-primary`.
- Decorative gradients are disallowed unless logged in `docs/design-exceptions.md`.

## Spacing, Radius, Hit Targets

- Grid: 8pt baseline.
- Allowed spacing increments: `4 / 8 / 16 / 24 / 32 / 48 / 64`.
- Default radius: `12px` (`--radius: 0.75rem`).
- Touch target minimum: `44x44`.
- Large CTA horizontal padding: `32px` each side.

## Typography

Typography scale is defined in Notion chapter 2.
Reference: [2 럂 䈀爀愀渀搀Ⰰ 氀愀礀漀甀琀 ☀ 琀漀欀攀渀猀崀⠀栀琀琀瀀猀㨀⼀⼀眀眀眀⸀渀漀琀椀漀渀⸀猀漀⼀㈀ⴀ䈀爀愀渀搀ⴀ氀愀礀漀甀琀ⴀ琀漀欀攀渀猀ⴀ㌀㐀㔀㐀㔀㐀㐀攀攀戀㐀㈀㠀㄀挀攀㤀㈀戀戀昀㜀攀戀㤀　搀昀㌀㠀㌀㔀㼀瀀瘀猀㴀㈀㄀⤀⸀਀਀吀伀䐀伀 ⠀圀攀攀欀 ㈀⤀㨀 椀渀氀椀渀攀 攀砀愀挀琀 栀攀愀搀椀渀最⼀戀漀搀礀 琀礀瀀攀 猀挀愀氀攀 愀渀搀 琀爀愀挀欀椀渀最 琀漀欀攀渀猀⸀਀਀⌀⌀ 䈀甀琀琀漀渀 䄀倀䤀 ⠀匀栀愀搀䌀一 䘀椀爀猀琀⤀਀਀䤀洀瀀漀爀琀 瀀愀琀栀㨀਀਀怀怀怀琀猀砀਀椀洀瀀漀爀琀 笀 䈀甀琀琀漀渀 紀 昀爀漀洀 ∀䀀⼀挀漀洀瀀漀渀攀渀琀猀⼀甀椀⼀戀甀琀琀漀渀∀㬀਀怀怀怀਀਀䄀瀀瀀爀漀瘀攀搀 挀愀氀氀 猀椀最渀愀琀甀爀攀猀㨀਀਀怀怀怀琀猀砀਀㰀䈀甀琀琀漀渀 瘀愀爀椀愀渀琀㴀∀搀攀昀愀甀氀琀∀ 猀椀稀攀㴀∀氀最∀㸀匀愀瘀攀 挀栀愀渀最攀猀㰀⼀䈀甀琀琀漀渀㸀਀㰀䈀甀琀琀漀渀 瘀愀爀椀愀渀琀㴀∀猀攀挀漀渀搀愀爀礀∀㸀䌀愀渀挀攀氀㰀⼀䈀甀琀琀漀渀㸀਀㰀䈀甀琀琀漀渀 瘀愀爀椀愀渀琀㴀∀最栀漀猀琀∀ 猀椀稀攀㴀∀猀洀∀㸀䐀椀猀洀椀猀猀㰀⼀䈀甀琀琀漀渀㸀਀㰀䈀甀琀琀漀渀 瘀愀爀椀愀渀琀㴀∀搀攀猀琀爀甀挀琀椀瘀攀∀㸀䐀攀氀攀琀攀 愀挀挀漀甀渀琀㰀⼀䈀甀琀琀漀渀㸀਀怀怀怀਀਀⌀⌀ 䈀甀琀琀漀渀 匀琀愀琀攀 䴀愀琀爀椀砀 ⠀䌀漀洀瀀愀挀琀⤀਀਀簀 䰀愀戀攀氀 簀 嘀愀爀椀愀渀琀 簀 䐀攀昀愀甀氀琀 簀 䠀漀瘀攀爀 簀 䐀椀猀愀戀氀攀搀 簀 倀爀攀猀猀攀搀 ⼀ 䘀漀挀甀猀 ⼀ 䰀漀愀搀椀渀最 ⼀ 匀攀氀攀挀琀攀搀 簀਀簀 ⴀⴀⴀ 簀 ⴀⴀⴀ 簀 ⴀⴀⴀ 簀 ⴀⴀⴀ 簀 ⴀⴀⴀ 簀 ⴀⴀⴀ 簀਀簀 䌀漀渀琀愀椀渀攀搀 簀 怀搀攀昀愀甀氀琀怀 簀 怀⌀㈀　㠀㘀㤀㈀怀 昀椀氀氀Ⰰ 眀栀椀琀攀 琀攀砀琀 簀 怀⌀㄀㘀㐀䘀㔀䈀怀 昀椀氀氀 簀 怀⌀䐀㄀䐀㔀䐀䈀怀 昀椀氀氀Ⰰ 怀⌀㤀䌀䄀㌀䄀䘀怀 琀攀砀琀 簀 䴀甀猀琀 攀砀椀猀琀 瀀攀爀 挀栀愀瀀琀攀爀 㐀 洀愀琀爀椀砀 簀਀簀 伀甀琀氀椀渀攀搀 簀 怀猀攀挀漀渀搀愀爀礀怀 簀 洀甀琀攀搀 戀漀爀搀攀爀Ⰰ 搀愀爀欀 琀攀砀琀 簀 眀愀猀栀 怀⌀䔀㔀䔀䄀䐀䘀怀 簀 洀甀琀攀搀 戀漀爀搀攀爀 ⬀ 怀⌀㤀䌀䄀㌀䄀䘀怀 琀攀砀琀 簀 䴀甀猀琀 攀砀椀猀琀 瀀攀爀 挀栀愀瀀琀攀爀 㐀 洀愀琀爀椀砀 簀਀簀 吀攀砀琀 簀 怀最栀漀猀琀怀 簀 琀爀愀渀猀瀀愀爀攀渀琀Ⰰ 搀愀爀欀 琀攀砀琀 簀 眀愀猀栀 怀⌀䔀㔀䔀䄀䐀䘀怀 簀 怀⌀㤀䌀䄀㌀䄀䘀怀 琀攀砀琀 簀 䴀甀猀琀 攀砀椀猀琀 瀀攀爀 挀栀愀瀀琀攀爀 㐀 洀愀琀爀椀砀 簀਀簀 䐀攀猀琀爀甀挀琀椀瘀攀 簀 怀搀攀猀琀爀甀挀琀椀瘀攀怀 簀 怀⌀䐀䌀㈀㘀㈀㘀怀 昀椀氀氀 簀 怀⌀䈀㤀㄀䌀㄀䌀怀 昀椀氀氀 簀 洀甀琀攀搀 渀攀甀琀爀愀氀猀 簀 䴀甀猀琀 攀砀椀猀琀 瀀攀爀 挀栀愀瀀琀攀爀 㐀 洀愀琀爀椀砀 簀਀਀䘀漀爀 昀甀氀氀 洀愀琀爀椀砀 爀漀眀猀Ⰰ 爀攀昀攀爀攀渀挀攀㨀 嬀㐀 숀· Components & patterns](https://www.notion.so/4-Components-patterns-3454544eeb4281479040ce5bd99406c7?pvs=21).

## Code-Level Do and Don't

```tsx
// Don't: raw hex in component code
<button style={{ backgroundColor: "#208692" }}>Save</button>

// Do: semantic component variant
<Button variant="default">Save</Button>
```

```tsx
// Don't: use destructive red for non-danger emphasis
<Badge className="bg-[#DC2626]">New</Badge>

// Do: use primary or neutral emphasis patterns
<Badge variant="secondary">New</Badge>
```

```tsx
// Don't: ad-hoc spacing outside 8pt increments
<div className="px-[30px] py-[13px]" />

// Do: snap to approved spacing steps
<div className="px-8 py-4" />
```

```tsx
// Don't: bypass focus visibility
<button className="outline-none">Submit</button>

// Do: keep visible focus ring
<Button className="focus-visible:ring-2 focus-visible:ring-ring">Submit</Button>
```

## Required States on Surfaces

Meaningful surfaces must define and ship:

- Loading
- Empty
- Error
- Success

Controls also require interaction states as documented in chapter 4.

## Accessibility Contract

- Keyboard path exists for all interactive flows.
- Focus indicators are visible and use semantic ring tokens.
- Contrast must meet WCAG AA for text and controls.
- Motion respects reduced-motion preferences.
- Hit area for interactive controls is at least `44x44`.
- Touch and pointer targets are not blocked by decorative layers.

## Import Paths and References

- ShadCN component path: `@/components/ui/*`.
- Token source of truth in code: `app/globals.css`.
- Figma library URL: `TODO_ADD_CANONICAL_FIGMA_LIBRARY_URL`.
- Notion canonical narrative and visuals: [UI/UX guidelines](https://www.notion.so/aosenuma-ai/UI-UX-guidelines-20be6c5f913d4f53ac0e76eb5e904eef?source=copy_link).

## Workflow (Design -> Code, Compact)

| Step | Action | Guardrail |
| --- | --- | --- |
| 0 | Onboard design model with repo + hub sections | Must match semantic color contract |
| 1 | Brief using UI inventory names | Use chapter 1 element taxonomy |
| 2 | Generate candidate frames | Reject raw hex or non-token spacing |
| 3 | Refine states and spacing | Require matrix states + 44x44 targets |
| 4 | Visual cross-check with style proof | Review embedded Figma/dated PNG evidence |
| 5 | Handoff to code | ShadCN-first implementation with checklist |
| 6 | Mirror final frames back | Keep Notion/Figma/code aligned |

Full workflow details: [6 럂 圀漀爀欀昀氀漀眀 ᐀†䌀氀愀甀搀攀 䐀攀猀椀最渀 馀‡䌀氀愀甀搀攀 䌀漀搀攀崀⠀栀琀琀瀀猀㨀⼀⼀眀眀眀⸀渀漀琀椀漀渀⸀猀漀⼀㘀ⴀ圀漀爀欀昀氀漀眀ⴀ䌀氀愀甀搀攀ⴀ䐀攀猀椀最渀ⴀ䌀氀愀甀搀攀ⴀ䌀漀搀攀ⴀ㌀㐀㜀㐀㔀㐀㐀攀攀戀㐀㈀㠀㄀㔀㘀㠀㜀　㈀攀㐀搀搀㜀㄀昀㠀㈀㔀愀㘀㼀瀀瘀猀㴀㈀㄀⤀⸀਀਀⌀⌀ 䔀砀挀攀瀀琀椀漀渀 倀爀漀挀攀猀猀਀਀䄀渀礀 搀攀瘀椀愀琀椀漀渀 昀爀漀洀 猀攀挀琀椀漀渀猀 愀戀漀瘀攀 洀甀猀琀 戀攀 氀漀最最攀搀 椀渀 怀搀漀挀猀⼀搀攀猀椀最渀ⴀ攀砀挀攀瀀琀椀漀渀猀⸀洀搀怀 戀攀昀漀爀攀 洀攀爀最攀⸀਀਀⌀⌀ 倀刀 䄀挀挀攀瀀琀愀渀挀攀 䌀栀攀挀欀氀椀猀琀਀਀怀怀怀洀搀਀ⴀ 嬀 崀 一漀 爀愀眀 栀攀砀 椀渀 挀栀愀渀最攀搀 唀䤀 昀椀氀攀猀 ⠀攀砀挀攀瀀琀 琀漀欀攀渀 搀攀昀椀渀椀琀椀漀渀猀 椀渀 最氀漀戀愀氀猀⸀挀猀猀⤀਀ⴀ 嬀 崀 匀栀愀搀䌀一 瘀愀爀椀愀渀琀猀 甀猀攀搀 昀漀爀 椀渀琀攀爀愀挀琀椀瘀攀 挀漀洀瀀漀渀攀渀琀猀਀ⴀ 嬀 崀 刀攀焀甀椀爀攀搀 猀琀愀琀攀猀 瀀爀攀猀攀渀琀 昀漀爀 渀攀眀 洀攀愀渀椀渀最昀甀氀 猀甀爀昀愀挀攀猀਀ⴀ 嬀 崀 䬀攀礀戀漀愀爀搀 瀀愀琀栀 愀渀搀 瘀椀猀椀戀氀攀 昀漀挀甀猀 瘀攀爀椀昀椀攀搀਀ⴀ 嬀 崀 㐀㐀砀㐀㐀 洀椀渀椀洀甀洀 栀椀琀 琀愀爀最攀琀 瘀攀爀椀昀椀攀搀਀ⴀ 嬀 崀 䘀椀最洀愀 昀爀愀洀攀 漀爀 搀愀琀攀搀 倀一䜀 瀀爀漀漀昀 氀椀渀欀攀搀 椀渀 倀刀਀ⴀ 嬀 崀 䄀渀礀 搀爀椀昀琀 氀漀最最攀搀 椀渀 搀漀挀猀⼀搀攀猀椀最渀ⴀ攀砀挀攀瀀琀椀漀渀猀⸀洀搀਀怀怀怀਀਀ഀ
```

```markdown
# design-exceptions.md

Use this log for any approved drift from `docs/design.md` or `app/globals.css`.

## Rules

- An exception must be opened before merge.
- Exceptions require an owner and expiry/review date.
- Permanent exceptions require a design system update PR.
- Closed exceptions should include resolution notes and links.

## Exception Entry Template

```md
## EXC-YYYYMMDD-###

- Date opened:
- Owner:
- Related PR:
- Scope (page/component/flow):
- Rule violated (link to design.md section):
- Reason:
- User impact if blocked:
- Screenshot or Figma link:
- Mitigation in this PR:
- Expiry/review date:
- Approval (name + date):
- Status: open | closed
- Resolution notes:
```

## Open Exceptions

_No open exceptions._

਍
```

```jsx
/**
 * ESLint rule: no-raw-hex
 * Flags direct hex colors in TSX/JSX code so teams use semantic tokens.
 * Intended as opt-in for staged adoption.
 */
"use strict";

const HEX_RE = /#[0-9a-fA-F]{3,8}\b/g;

module.exports = {
  meta: {
    type: "problem",
    docs: {
      description: "Disallow raw hex colors in JSX/TSX code",
      recommended: false,
    },
    schema: [],
    messages: {
      noRawHex:
        "Raw hex color '{{value}}' is not allowed. Use semantic tokens or approved variants.",
    },
  },

  create(context) {
    const filename = context.getFilename().replace(/\\/g, "/");
    if (filename.endsWith("app/globals.css") || filename.endsWith("docs/design.md")) {
      return {};
    }

    function reportStringLiteral(node, text) {
      const matches = text.match(HEX_RE);
      if (!matches) return;
      matches.forEach((value) => {
        context.report({
          node,
          messageId: "noRawHex",
          data: { value },
        });
      });
    }

    return {
      Literal(node) {
        if (typeof node.value === "string") {
          reportStringLiteral(node, node.value);
        }
      },
      TemplateElement(node) {
        if (typeof node.value?.raw === "string") {
          reportStringLiteral(node, node.value.raw);
        }
      },
      JSXAttribute(node) {
        if (node.name?.name !== "style") return;
        context.report({
          node,
          message:
            "Inline style usage is discouraged for colors. Prefer semantic class tokens or component variants.",
        });
      },
    };
  },
};

਍
```

```markdown
# Custom ESLint Rules

## `no-raw-hex` (opt-in)

Rule file: `eslint-rules/no-raw-hex.js`

Purpose:
- Prevent direct hex colors in JSX/TSX code.
- Encourage semantic tokens and ShadCN variants from `docs/design.md`.

### Enable in `.eslintrc.cjs`

```js
const noRawHexRule = require("./eslint-rules/no-raw-hex");

module.exports = {
  plugins: ["local"],
  rules: {
    "local/no-raw-hex": "warn",
  },
  settings: {
    "import/resolver": {
      node: true,
    },
  },
  overrides: [
    {
      files: ["**/*.{js,jsx,ts,tsx}"],
      plugins: ["local"],
      rules: {
        "local/no-raw-hex": "warn",
      },
    },
  ],
};
```

### If you use `eslint-plugin-local-rules`

Configure `eslint-local-rules.js`:

```js
module.exports = {
  "no-raw-hex": require("./eslint-rules/no-raw-hex"),
};
```

Then use:

```js
rules: {
  "local-rules/no-raw-hex": "warn",
}
```

Keep this rule as `warn` initially, then upgrade to `error` after cleanup.

਍
```

```jsx
import fs from "node:fs";
import path from "node:path";

const root = process.cwd();
const designPath = path.join(root, "docs", "design.md");
const globalsPath = path.join(root, "app", "globals.css");

function readFileOrExit(filePath) {
  if (!fs.existsSync(filePath)) {
    console.error(`Missing required file: ${filePath}`);
    process.exit(1);
  }
  return fs.readFileSync(filePath, "utf8");
}

function extractCssVars(cssText) {
  const normalized = cssText.replace(/\0/g, "");
  const regex = /--([a-z0-9-]+)\s*:/gi;
  const out = new Set();
  let match;
  while ((match = regex.exec(normalized)) !== null) {
    out.add(match[1]);
  }
  return out;
}

function extractDesignTokenBlockVars(markdownText) {
  const normalized = markdownText.replace(/\0/g, "");
  const blockRegex = /```css\s*([\s\S]*?)```/gi;
  let match;
  while ((match = blockRegex.exec(normalized)) !== null) {
    const content = match[1];
    if (content.includes(":root")) {
      return extractCssVars(content);
    }
  }
  return new Set();
}

function diffSets(a, b) {
  return [...a].filter((item) => !b.has(item)).sort();
}

const designMd = readFileOrExit(designPath);
const globalsCss = readFileOrExit(globalsPath);

const designVars = extractDesignTokenBlockVars(designMd);
const globalVars = extractCssVars(globalsCss);

if (designVars.size === 0) {
  console.error("No :root CSS token block found in docs/design.md");
  process.exit(1);
}

if (globalVars.size === 0) {
  console.error("No CSS variables found in app/globals.css");
  process.exit(1);
}

const onlyInDesign = diffSets(designVars, globalVars);
const onlyInGlobals = diffSets(globalVars, designVars);

if (onlyInDesign.length || onlyInGlobals.length) {
  console.error("Token drift detected between docs/design.md and app/globals.css");
  if (onlyInDesign.length) {
    console.error("\nIn docs/design.md only:");
    onlyInDesign.forEach((item) => console.error(`  - --${item}`));
  }
  if (onlyInGlobals.length) {
    console.error("\nIn app/globals.css only:");
    onlyInGlobals.forEach((item) => console.error(`  - --${item}`));
  }
  process.exit(1);
}

console.log(`Token drift check passed (${designVars.size} tokens in sync).`);
```

```jsx
module.exports = {
  root: true,
  extends: [],
  rules: {},
};

```