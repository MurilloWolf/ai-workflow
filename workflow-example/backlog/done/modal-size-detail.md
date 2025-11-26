# Fix Size of modal for Detail Componente on /Calendar page

## 1. Metadata

- **Backlog ID / Incident Link**: 1
- **Bug Title**:
- **Severity**: Major
- **Owner**:
- **Reported By**:
- **Environments Affected**: View Race Detail Modal on /Calendar page

## 2. Current Behavior

Using a mobile device, when opening the page /calendar and click on a race to view details, the modal is not properly sized for smaller screens, making it difficult to read the content and navigate within the modal.

This same issue occurs when we click on the calendar event, when we have more than 3 events on the same day, the modal opens to select a race to view details, and the modal is not properly sized for smaller screens.

## 3. Expected Behavior

The modal should be responsive and adapt its size based on the screen dimensions. On smaller screens, it should occupy a larger portion of the viewport to ensure that all content is easily readable and accessible. The modal should also allow for scrolling if the content exceeds the available space.

## 4. Reproduction Steps

1. Open the application on a mobile device or use a browser's developer tools to simulate a mobile viewport.
2. Navigate to the /calendar page.
3. Click on event on the calendar
4. Observe the size of the modal that appears and how it fits within the screen.

## 5. Root Cause Hypothesis

Wrogn CSS styles or classes applied to the modal component that do not account for responsiveness or proper sizing on smaller screens. The modal may have fixed width/height values or lack media queries to adjust its dimensions based on the viewport size.

## 6. Fix Plan by Layer

- **Presentation**: Adjust `DialogContent` sizing in `components/system/Calendar/Event/Detail.tsx` to use fluid widths and allow vertical scrolling on narrow screens while keeping the desktop split layout intact. Update the list modal container in `components/system/Calendar/Event/ListModal.tsx` to adopt the same responsive constraints.
- **Translation**: No new copy; reuse existing calendar strings.
- **Application / Domain**: No changes; analytics hooks continue to operate through `useAnalytics`.
- **Infrastructure**: No external calls affected.

## 7. Safeguards & Regression Considerations

- Verify that both modals still open/close correctly via keyboard and backdrop interactions.
- Confirm analytics events (`trackRaceView`, `trackRaceLocationClick`, `trackRaceRegistrationClick`) continue to fire when the detail modal opens.
- Spot-check the shadcn `Dialog` primitive elsewhere to ensure the responsive overrides remain scoped to these components only.

## 9. Execution Log

| Timestamp            | Update                                                                                                                                  |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| 2025-11-25 21:05 UTC | Reviewed `Detail` and `ListModal` implementations; confirmed fixed-width classes prevented mobile responsiveness.                       |
| 2025-11-25 21:27 UTC | Added responsive width/height constraints and mobile scrolling behavior; `npm run lint` passed, `npm run test` unavailable (no script). |
| 2025-11-25 22:10 UTC | Re-centered modals with reduced widths, added safe-area padding tweaks with dark backgrounds, and reran `npm run lint` (pass).          |
| 2025-11-25 22:40 UTC | Swapped the list modal to shadcn `Dialog` for full-screen overlay coverage, adjusted safe-areas, and enforced `min-h-screen` on calendar containers; `npm run lint` passed. |
| 2025-11-25 23:05 UTC | Added an opt-in `className` to `MashGradiant` so only the calendar view enforces `min-h-screen` (restoring CTA overlay sizing) and reran `npm run lint` (pass). |

## 10. Validation Checklist

- [ ] Bug reproduced on main branch
- [ ] Fix verified in dev environment (EN & PT)
- [ ] Manual QA (edge cases + server actions) completed
- [ ] Related shadcn/system components still behave as expected elsewhere
- [ ] Logs/metrics monitored for regressions

## 11. Closeout

- [x] `npm run lint` successful
- [ ] `/workflow` documentation updated with any new learnings or rules
- [x] `/pipeline` updated with final summary and linked PR
- [ ] Follow-up tasks (if needed) added to `/workflow/backlog`
