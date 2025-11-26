# Pipeline Usage Guide

The `/workflow/pipeline` directory always contains the single task currently being executed by the Workflow Agent. At any moment there should be exactly one active pipeline entry—remove or archive the previous entry only after it is completed and documented.

## Creating a Pipeline Entry

1. Pick the correct template (feature vs. fix) from this folder.
2. Copy the template into a new markdown file named with the date and short slug, e.g., `2025-11-25-add-purchase-flow.md`.
3. Fill out every section before beginning implementation. If information is unknown, log the open question explicitly.
4. Keep the file updated as work progresses; it is the living source of truth for the in-flight task.
5. When the task is complete, ensure the "Closeout" checklist is satisfied, then summarize any new rules in `/workflow/agent.md` (or a relevant `/workflow` note) before deleting or archiving the entry.

## Required Sections

- **Metadata** – backlog ID, priority, owner, target release, and translation scope.
- **Current Context** – snapshot of related decisions, references to `/workflow/backlog`, and links to design/product notes.
- **Plan** – ordered steps mapped to layers (Presentation → Translation → Application → Domain → Infrastructure). Note required interfaces/ports.
- **Implementation Log** – timestamped updates so reviewers can follow the work.
- **Localization Plan** – English/PT keys to add, plus verification steps.
- **QA Evidence** – manual QA protocol results (Section 8 of the charter) with screenshots or notes.
- **Closeout** – confirmation that `/workflow` docs were updated, lint passed, and anything deferred was re-added to `/backlog`.

## Templates

- [`feature-template.md`](./template/feature-template.md) – use for net-new capabilities or enhancements.
- [`fix-template.md`](./template/fix-template.md) – use for bug fixes, regressions, or hotfixes.

Always keep the pipeline entry concise but complete—the agent should be able to resume work or hand off the task using this file alone.
