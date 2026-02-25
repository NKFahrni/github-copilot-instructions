# UI -- Angular 19+ (TypeScript)

## Overview

Frontend application built with Angular 19+ using strict TypeScript
settings.

Architecture principles:

-   DRY
-   SOLID
-   Standalone components
-   Smart / Presentational separation
-   OnPush change detection
-   Minimal dependencies

------------------------------------------------------------------------

## Tech Stack

-   Angular 19+
-   TypeScript (strict mode)
-   RxJS
-   Angular Signals (where appropriate)
-   ESLint
-   Jasmine or Jest

------------------------------------------------------------------------

## Architectural Guidelines

### Separation of Concerns

-   Components handle UI logic only.
-   Services contain business logic.
-   API calls never live inside components.
-   No domain logic in templates.

### SOLID Enforcement

-   SRP: One responsibility per class/service.
-   OCP: Prefer composition over modification.
-   LSP: Honour interface contracts.
-   ISP: Avoid fat interfaces.
-   DIP: Depend on abstractions.

### State Strategy

-   Local UI state → Signals.
-   Async streams → RxJS.
-   No manual subscriptions without teardown.
-   Prefer async pipe or takeUntilDestroyed.

------------------------------------------------------------------------

## Project Structure

    src/
     ├── app/
     │   ├── core/
     │   ├── shared/
     │   ├── features/
     │   └── app.config.ts

------------------------------------------------------------------------

## Development

``` bash
npm install
ng serve
ng build
```

------------------------------------------------------------------------

## Definition of Done

-   Strict TypeScript passes
-   Lint passes
-   No memory leaks
-   Tests added
-   No unnecessary dependencies introduced
