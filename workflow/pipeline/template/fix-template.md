# Fix Pipeline Entry Template

> Copy this template, rename it with the date + short slug (e.g., `2025-11-25-fix-checkout-error.md`), and complete all fields before starting remediation.

## 1. Metadata

- **Backlog ID / Incident Link**:
- **Bug Title**:
- **Severity**: <!-- Blocker / Critical / Major / Minor -->
- **Owner**:
- **Reported By**:
- **Environments Affected**:

## 2. Current Behavior

Describe the observed issue, including screenshots/log excerpts if available.

## 3. Expected Behavior

Clarify what should happen instead.

## 4. Reproduction Steps

1. Step 1
2. Step 2
3. Step 3

## 5. Root Cause Hypothesis

Document suspected root cause, relevant modules, and any supporting evidence.

## 6. Fix Plan by Layer

| Layer                  | Planned Change | Notes |
| ---------------------- | -------------- | ----- |
| Presentation           |
| Translation            |
| Application / Services |
| Domain                 |
| Infrastructure         |

## 7. Safeguards & Regression Considerations

List additional validation, feature flags, monitoring, or analytics updates required.

## 8. Localization Impact

| Key | EN Copy | PT Copy | Status |
| --- | ------- | ------- | ------ |

## 9. Execution Log

| Timestamp | Update |
| --------- | ------ |

## 10. Validation Checklist

- [ ] Bug reproduced on main branch
- [ ] Manual QA (edge cases + server actions) completed
- [ ] Logs/metrics monitored for regressions

## 11. Closeout

- [ ] `npm run lint` successful
- [ ] `/workflow` documentation updated with any new learnings or rules
- [ ] `/pipeline` updated with final summary and linked PR
- [ ] Follow-up tasks (if needed) added to `/workflow/backlog`
