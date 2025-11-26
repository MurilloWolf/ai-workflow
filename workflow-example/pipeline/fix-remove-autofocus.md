# Fix autofocus on input fields in Purchase Modal (free and paid)

## 1. Metadata

- **Backlog ID / Incident Link**: 2
- **Bug Title**: Fix autofocus on input fields in Purchase Modal (free and paid)
- **Severity**: <!-- Blocker / Critical / Major / Minor -->
- **Owner**:
- **Reported By**:
- **Environments Affected**:

## 2. Current Behavior

When users open the purchase modal for free or paid products, the input fields receive autofocus automatically. This can stand on desktop aplication, but on mobile devices, it often triggers the on-screen keyboard to appear, which can obstruct the view of the modal and lead to a poor user experience.

## 3. Expected Behavior

The input fields in the purchase modal should not receive autofocus automatically when the modal is opened. Users should be able to manually select the input fields as needed, ensuring that the on-screen keyboard does not appear unexpectedly on mobile devices.

This must be applied to both free and paid product purchase modals across the application.

## 4. Reproduction Steps

1. Open the application on a mobile device or use a browser's developer tools to simulate a mobile viewport.
2. Navigate to a coach page or training-sheet page.
3. Click on a free or paid product to open the purchase modal.
4. Observe that the input fields receive autofocus automatically, causing the on-screen keyboard to appear.

## 5. Root Cause Hypothesis

`@radix-ui/react-dialog` automatically calls `focus()` on the first focusable element inside the modal when it opens. In our purchase flow that first element is one of the customer info inputs (name/email), so the keyboard pops up immediately on mobile. `PurchaseDialog` did not override `onOpenAutoFocus`, so every free/premium modal inherited that behavior.

## 6. Fix Plan by Layer

| Layer                  | Planned Change                                           | Notes                                                                                                      |
| ---------------------- | -------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Presentation           | Prevent the dialog from auto focusing any field on open. | Add a `disableAutoFocus` option to `PurchaseDialog` and default it to true so all purchase modals opt out. |
| Translation            | _No changes_                                             |                                                                                                            |
| Application / Services | _No changes_                                             |                                                                                                            |
| Domain                 | _No changes_                                             |                                                                                                            |
| Infrastructure         | _No changes_                                             |                                                                                                            |

## 7. Safeguards & Regression Considerations

- Verify that input fields in purchase modals no longer receive autofocus automatically on both desktop and mobile devices.

## 8. Localization Impact

| Key | EN Copy | PT Copy | Status |
| --- | ------- | ------- | ------ |

## 9. Execution Log

| Timestamp            | Update                                                                                                                                       |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| 2025-11-25 15:20 BRT | Confirmed Radix dialog auto-focus behavior and updated `PurchaseDialog` to prevent it via `onOpenAutoFocus`. Ran `npm run lint` to validate. |

## 10. Validation Checklist

- [ ] Bug reproduced on main branch
- [ ] Fix verified in dev environment (EN & PT)
- [ ] Manual QA (edge cases + server actions) completed
- [ ] Related shadcn/system components still behave as expected elsewhere
- [ ] Logs/metrics monitored for regressions

## 11. Closeout

- [x] `npm run lint` successful
- [ ] `/workflow` documentation updated with any new learnings or rules
- [ ] `/pipeline` updated with final summary and linked PR
- [ ] Follow-up tasks (if needed) added to `/workflow/backlog`
