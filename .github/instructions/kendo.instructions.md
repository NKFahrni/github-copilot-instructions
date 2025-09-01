# Kendo UI Component Rules

## Kendo Grid (Typed + Performant)
- Types: `GridDataResult` for data; `State` for paging/sorting/filtering.
- Client ops: `process(items, state)` from `kendo-data-query`.
- Server ops: send `State` to backend and bind `Observable<GridDataResult>`.
- Use virtualization/paging for large datasets.

## Code Quality & Style
- **SOLID**: single responsibility, clear abstractions, dependency inversion via DI.
- **Naming**:
  - `SCREAMING_SNAKE_CASE` for constants.
  - `camelCase` for variables and functions.
  - No abbreviations; prefer descriptive names.
- **No magic numbers/strings**: extract to named constants.
- **DRY after 2–3 repeats**: refactor into small utilities/services.
- Keep functions small, pure, and strongly typed.

## Tooling Compliance
- Output must be ESLint-clean and Prettier-formatted.
- Do not generate or fill any `*.spec.ts` files.

## Folder Structure
- Follow the **existing project structure** exactly; do not create new directories or move files unless explicitly requested.

## SCSS
- do not add custom scss unless i tell you to. Kendo ui components are styled using the built-in themes and customization options provided by the library.
