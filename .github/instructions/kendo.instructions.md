# Kendo UI for Angular Component Instructions

## Overview
This project uses Angular for building UI components with extensive integration of Kendo UI components for rich, interactive interfaces. Templates are written in HTML and integrate Kendo UI elements for forms, dialogs, grids, uploads, and advanced data visualization.

## Angular + Kendo UI Component Structure

### 1. Component Architecture
- **TypeScript Class**: Defines logic, state, event handlers, and data management.
- **HTML Template**: Contains UI markup using Angular directives integrated with Kendo UI components.
- **SCSS/CSS**: Minimal custom styles (rely on Kendo themes).

### 2. Kendo UI Module Imports
- Import required Kendo UI modules in the component's `imports` array:
  ```typescript
  imports: [
    KENDO_UPLOADS,
    KENDO_BUTTON, 
    KENDO_DIALOGS,
    KENDO_GRID,
    KENDO_DROPDOWNS,
    KENDO_PROGRESSBAR,
    // ... other Kendo modules
  ]
  ```

### 3. Template Integration Patterns
Use Kendo UI components with Angular binding patterns:
```html
<!-- Dialogs with dynamic properties -->
<kendo-dialog [title]="dialogTitle" [minWidth]="450" [visible]="showDialog">
  <kendo-upload 
    [saveUrl]="uploadSaveUrl" 
    [restrictions]="uploadRestrictions"
    (upload)="onFileUpload($event)">
  </kendo-upload>
  
  <kendo-progressbar [value]="uploadProgress"></kendo-progressbar>
  
  <button kendoButton 
    [primary]="true" 
    (click)="startUpload()"
    [disabled]="!canUpload">
    Upload Files
  </button>
</kendo-dialog>

<!-- Dropdowns with data binding -->
<kendo-dropdownlist
  [data]="categories"
  [textField]="'name'"
  [valueField]="'id'"
  [(ngModel)]="selectedCategoryId"
  (selectionChange)="onCategoryChange($event)">
</kendo-dropdownlist>
```

### 4. Angular Control Flow with Kendo UI
Use Angular's modern control flow directives:
```html
@if (showGrid) {
  <kendo-grid [data]="gridData" [sortable]="true" [pageable]="true">
    <kendo-grid-column field="name" title="Name"></kendo-grid-column>
    <kendo-grid-column field="category" title="Category"></kendo-grid-column>
  </kendo-grid>
}

@for (item of menuItems; track item.id) {
  <kendo-button (click)="selectItem(item)">{{ item.name }}</kendo-button>
}
```

## Kendo Grid (Typed + Performant)
- **Types**: Use `GridDataResult` for data binding; `State` for paging/sorting/filtering operations.
- **Client operations**: Use `process(items, state)` from `kendo-data-query` for local data processing.
- **Server operations**: Send `State` object to backend and bind `Observable<GridDataResult>` to grid.
- **Performance**: Use virtualization and paging for large datasets (>1000 records).
- **Columns**: Define strongly-typed column configurations with proper field bindings.

## Event Handling Best Practices
- Bind Kendo UI events to TypeScript methods using Angular event syntax:
  ```typescript
  // Template
  (selectionChange)="onSelectionChange($event)"
  (upload)="onFileUpload($event)"
  (close)="onDialogClose()"
  
  // Component
  onSelectionChange(event: SelectionEvent): void {
    this.selectedItem = event.selectedRows[0]?.dataItem;
  }
  ```

## Code Quality & Style
- **SOLID**: Single responsibility, clear abstractions, dependency inversion via DI.
- **Naming**:
  - `SCREAMING_SNAKE_CASE` for constants.
  - `camelCase` for variables and functions.
  - `PascalCase` for types and component classes.
  - No abbreviations; prefer descriptive names (e.g., `uploadProgress` not `uploadProg`).
- **No magic numbers/strings**: Extract to named constants.
- **DRY after 2–3 repeats**: Refactor into small utilities/services.
- Keep functions small, pure, and strongly typed.
- Use Angular's dependency injection for Kendo UI services.

## Tooling Compliance
- Output must be ESLint-clean and Prettier-formatted.
- Do not generate or fill any `*.spec.ts` files.
- Follow Angular and Kendo UI TypeScript patterns.

## Folder Structure
- Follow the **existing project structure** exactly; do not create new directories or move files unless explicitly requested.
- Organize Kendo UI components within existing Angular component hierarchy.

## SCSS Restrictions
- **Do not add custom SCSS** unless explicitly requested.
- Kendo UI components are styled using built-in themes and customization options provided by the library.
- Use Kendo theme variables and CSS custom properties for any necessary customizations.
- Rely on Kendo's responsive design and accessibility features.

## Data Binding Patterns
- Use Angular's reactive forms with Kendo UI form components.
- Implement proper validation using Angular validators with Kendo UI input components.
- Use observables and signals for reactive data updates with Kendo UI components.
- Maintain type safety between Angular models and Kendo UI component data properties.
