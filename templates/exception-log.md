# Exception log

Approved deviations from the rules in [`DESIGN.md`](../DESIGN.md). Copy this file into your project. Brand-wide constraints belong in the brand book's "Constraints and exceptions" section instead.

| ID | Date | Scope | Rule ID | Deviation | Reason | User impact and mitigation | Approved by | Owner | Review or expiry date | Status |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| EX-001 | `[YYYY-MM-DD]` | `[SCREEN, COMPONENT, OR RELEASE]` | `[RULE ID]` | `[WHAT DIFFERS]` | `[WHY]` | `[IMPACT; HOW IT'S REDUCED]` | `[NAME OR ROLE]` | `[NAME]` | `[DATE]` | `[OPEN / CLOSED]` |

## Rules for exceptions

- No deviation from a MUST rule without an entry here.
- Exceptions to accessibility rules need a mitigation and a fix date.
- Every exception is reviewed by its date: remove it, extend it with a reason, or propose a rule change ([`docs/customization.md`](../docs/customization.md#changing-a-rule)).
- When the same exception keeps coming back, change the rule instead.

## Requesting an exception

1. Name the rule ID and explain why it doesn't work in this case.
2. Describe the alternative and its effect on users, including accessibility.
3. Get approval from the person responsible for the rules.
4. Add a row above and link it from the pull request or prototype.
