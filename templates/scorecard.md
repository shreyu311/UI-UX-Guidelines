# Audit scorecard

Copy this file for each audit. Scoring and severity are defined in [`docs/validation.md`](../docs/validation.md#scored-audits).

| Field | Value |
| --- | --- |
| Product or prototype set | `[NAME]` |
| Build, version, or link | `[VERSION OR LINK]` |
| Audit date | `[YYYY-MM-DD]` |
| Auditor(s) | `[NAMES]` |
| `DESIGN.md` version | `[VERSION]` |
| Brand book used | `[FILE OR "none, fallbacks"]` |

## Results by checklist group

| Group | Passed | Applicable | Score |
| --- | --- | --- | --- |
| Brand and tokens | | | % |
| Color | | | % |
| Typography | | | % |
| Layout and responsive behavior | | | % |
| Components and states | | | % |
| Interaction and motion | | | % |
| Navigation | | | % |
| Content | | | % |
| Accessibility | | | % |
| Prototypes (if applicable) | | | % |
| **Overall** | | | **%** |

Score = passed ÷ applicable × 100. Change since the previous audit: `[+/- POINTS]`.

## Failures

| Rule ID | Where | Issue | Severity | Owner | Due | Status |
| --- | --- | --- | --- | --- | --- | --- |
| `[e.g. CLR-1]` | `[SCREEN OR COMPONENT]` | `[WHAT FAILS]` | `[CRITICAL / MAJOR / MINOR]` | `[NAME]` | `[DATE]` | `[OPEN / FIXED]` |

## Not tested

List checks that weren't performed, so they aren't mistaken for passes.

| Check | Reason |
| --- | --- |
| `[e.g. screen reader]` | `[REASON]` |

## Recommendation

- [ ] Ready
- [ ] Ready once Critical items are fixed
- [ ] Not ready; re-audit after fixes

Notes: `[NOTES]`
