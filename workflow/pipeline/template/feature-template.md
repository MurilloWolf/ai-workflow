# Feature Pipeline Entry Template

> Duplicate this file, rename it with the date + short slug (e.g., `2025-11-25-new-tracker-widget.md`), and fill in every section before handing the task to the Workflow Agent.

## 1. Metadata

- **Backlog ID**: <!-- link to /workflow/backlog entry -->
- **Feature Name**:
- **Priority**: <!-- High / Medium / Low -->
- **Owner**:
- **Target Release / Sprint**:
- **Locales Impacted**: <!-- EN/PT or others -->

## 2. Problem Statement

Describe the customer or business problem this feature solves. Reference any docs/specs.

## 3. Success Criteria

- [ ] Criterion 1
- [ ] Criterion 2
- [ ] Criterion 3

## 4. Architecture & Layer Plan

| Layer                         | Change Summary | Interfaces / Ports Needed |
| ----------------------------- | -------------- | ------------------------- |
| Presentation (app/components) |                |                           |
| Translation                   |                |                           |
| Application / Services        |                |                           |
| Domain                        |                |                           |
| Infrastructure                |                |                           |

## 5. Dependencies & Risks

List upstream/downstream dependencies, migrations, env vars, or tooling constraints.

## 6. Localization Plan

| Key | English Copy | Portuguese Copy | File |
| --- | ------------ | --------------- | ---- |

## 7. Implementation Checklist

- [ ] Ports/interfaces defined
- [ ] Server actions outlined (if applicable)
- [ ] Styling scoped locally (no global CSS)
- [ ] Data contracts/DTOs confirmed

## 8. Execution Log

| Timestamp | Update |
| --------- | ------ |

## 9. Manual QA Evidence

Summaries, screenshots, or notes covering both locales, edge cases, and server actions per the charter.

## 10. Closeout

- [ ] `npm run lint` successful
- [ ] `/workflow` documentation updated with new rules/process
- [ ] `/pipeline` status updated to "Done" with summary
- [ ] Follow-up work (if any) added back to `/workflow/backlog`
