# Workflow Agent Charter

## 1. Purpose and Location

- The Workflow Agent lives entirely under `/workflow/agent` and governs how the project automation operates.
- `/backlog` tracks prioritized upcoming work; `/pipeline` holds the single task currently in progress. Treat those files as the source of truth for sequencing.
- Every action the agent takes must be justified by information inside `/workflow` (never rely on memory or external context).

## 2. Operating Loop

1. **Intake** – Read `/pipeline` to understand the active task. Cross-check `/backlog` for prerequisites or dependencies. Capture any constraints already documented in `/workflow`.
2. **Plan** – Break the task into steps respecting CLEAN Architecture layers (Presentation → Application → Domain → Infrastructure). Identify required interfaces/ports before touching implementation.
3. **Execute** – Implement from the domain layer outward, keeping business logic isolated.
4. **Validate** – Run `npm run lint`, `npm run test`, and any task-specific scripts. Do not mark work as complete until all checks pass.
5. **Report** – Update `/pipeline` with status, blockers, or next actions. When closing a pipeline entry, capture the change inside the project documentation (`/workflow/agent.md` or the relevant `/workflow` note) so the new rule/process is preserved before marking the task complete.

## 3. Coding Standards

- **TypeScript**: `strict: true`, `noImplicitAny`, `noUnusedLocals`, `noUnusedParameters`, `exactOptionalPropertyTypes`. Favor pure functions and immutable data.
- **Naming**: PascalCase for classes/types, camelCase for variables/functions, kebab-case for file names unless framework conventions differ. Constants that are truly global use `UPPER_SNAKE_CASE`.
- **Interfaces & Ports**: Every external dependency (HTTP, DB, LLM, storage) must be accessed via an interface defined in the Application or Domain layer. Concrete adapters live in Infrastructure.
- **Error Handling**: Never swallow errors. Propagate domain errors explicitly (value objects or `Result` types) and log infrastructure failures with actionable context.
- **Formatting & Lint**: ESLint with `@typescript-eslint/recommended`, `no-floating-promises`, `prefer-const`, `no-misused-promises`. Prettier governs formatting (2 spaces, trailing commas, single quotes if consistent with repo). Husky or equivalent must block commits when lint/tests fail.
- **Comments**: Avoid inline or block comments in source files. Only document via JSDoc when the public contract would otherwise be unclear.

## 4. UI, Components, and Styling

- Prefer shadcn UI primitives located under `components/ui` before inventing custom elements.
- Reusable application-specific components belong in `components/system`; do not scatter them elsewhere.
- Never modify `app/globals.css`. Scope styling through component-level classes, Tailwind utilities, or module styles local to the component being touched.
- Keep translation keys and locale data close to their usage by updating both English and Portuguese message files before rendering new copy.

## 5. Server Actions and BFF Guidance

- When adding server-driven behavior for UI flows, prefer Next.js server actions instead of standalone API routes.
- Server actions must orchestrate domain/application services via well-defined interfaces and should not embed business logic directly.
- Treat server actions as the primary BFF surface: validate inputs, delegate to use cases, and return DTOs already shaped for the requesting UI.

## 6. Rules of Engagement

### Always Do

- Uphold SOLID: SRP in services/use cases, DIP via constructor injection, ISP by keeping interfaces focused.
- Apply DRY by extracting shared logic into reusable functions or value objects instead of copying blocks.
- Write unit tests for every use case and adapter. Cover success, failure, and edge cases using builders/fixtures to keep tests expressive.
- Document new decisions or deviations immediately inside `/workflow` so other contributors can trace context.
- Confirm every new user-facing string exists in both locales before the feature ships.

### Never Do

- Added external libraries without approval
- Run commands on the system, even for testing
- Implement business logic inside UI components, controllers, or adapters.
- Call external providers directly from Domain/Application; always go through a port/interface.
- Introduce magic numbers/strings. Move them into constants or configuration modules with descriptive names.
- Disable lint rules to “make it pass” or merge with failing tests.
- Bypass the checklist in Section 7.
- Use `any` or `unknown` on TypeScript types to circumvent type safety.
- Comment code, if is extremilly necessary comment using JsDoc or similar.

## 7. Quick Checklist Before Marking a Task Done

- [ ] `/pipeline` reviewed, understood, and updated with latest status.
- [ ] Dependencies verified against `/backlog`.
- [ ] Lint (`npm run lint`) and tests (`npm run test`) passing locally.
- [ ] Documentation under `/workflow` reflects any new rules, assumptions, or decisions.
- [ ] Finishing the pipeline entry also includes updating the project documentation in `/workflow` with the resulting change.
- [ ] UI changes rely on shadcn or `components/system`; styling scoped locally (no global CSS edits).
- [ ] Created/updated tests for new/changed functionality.

Adhering to this charter keeps the Workflow Agent predictable, auditable, and aligned with CLEAN Architecture, SOLID, and DRY principles across the codebase.
