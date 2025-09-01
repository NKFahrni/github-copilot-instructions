# Copilot Instruction Set

This repository contains curated instruction sets to guide AI-assisted development within our Angular projects. The goal is to ensure **consistency, performance, and adherence to best practices** when generating code with GitHub Copilot or similar AI tools.

---

## 📂 Repository Structure

- **`general.instructions.md`**  
  Core rules and conventions for all Angular development in this project:
  - Follow Angular version from `package.json`  
  - Standalone components, signals, new control flow (`@if/@for/@switch`)  
  - SOLID principles, naming conventions, and strict TypeScript usage  
  - RxJS best practices and observable handling  
  - ESLint + Prettier compliance  
  - Respecting existing project structure  

- **`kendo.instructions.md`**  
  Specific guidelines for **Kendo UI component usage**:
  - Typed + performant `KendoGrid` setup (client & server ops)  
  - Naming, DRY, and code quality rules  
  - Tooling compliance (lint + format)  
  - SCSS restrictions (use Kendo themes)  

- **`angular.instructions.md`**  
  Persona-based instruction set targeting **Angular v20+** and cutting-edge practices:
  - Signals for state management (`signal`, `computed`, `update`)  
  - Standalone components with OnPush change detection  
  - Modern templates using native control flow  
  - Service patterns with `inject()` and `providedIn: 'root'`  
  - RxJS integration (no manual `subscribe()`, use `toSignal`, `| async`)  
  - Strong typing, clean architecture, performance optimization  

---

## 🚀 How to Use

1. **Load into Copilot**: Use these instruction files as **system prompts** or reference guidelines when working with AI-assisted code generation.  
2. **Project-Specific Rules**: Always combine `general.instructions.md` with either `kendo.instructions.md` (when working on UI components) or `angular.instructions.md` (for modern Angular features).  
3. **Consistency**: Generated code must follow these instructions:
   - No `any` types; prefer `unknown` + narrowing.  
   - No `ngClass`/`ngStyle` → use native property bindings.  
   - No new directories unless explicitly required.  
   - ESLint + Prettier clean output.  

---

## 🔑 Principles

- **Maintainability**: Small, focused components and services.  
- **Performance**: Signals, OnPush, virtualization for grids.  
- **Clarity**: Explicit naming, no abbreviations, no magic numbers.  
- **Consistency**: Follow Angular style guide + project conventions.  

---

## 📖 Resources

- [Angular Components](https://angular.dev/essentials/components)  
- [Angular Signals](https://angular.dev/essentials/signals)  
- [Angular Templates](https://angular.dev/essentials/templates)  
- [Angular DI](https://angular.dev/essentials/dependency-injection)  
- [Angular Style Guide](https://angular.dev/style-guide)  
- [Kendo UI Docs](https://www.telerik.com/kendo-angular-ui/components/)  

---

## ✅ Output Expectations

When using these instruction sets, Copilot should generate code that is:

- **Angular version aligned** (from `package.json`)  
- **Typed, clean, maintainable**  
- **ESLint + Prettier compliant**  
- **Respectful of project structure**  
- **Production-ready without post-cleanup**  
