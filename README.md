# GitHub Copilot Instructions

This repository contains curated instruction sets to guide AI-assisted development across multiple technology stacks. The goal is to ensure **consistency, performance, and adherence to best practices** when generating code with GitHub Copilot or similar AI tools.

## 📑 Table of Contents

- [General Instructions](#-general-instructions)
  - [Git Workflow](#git-workflow)
- [Angular Development](#-angular-development)
  - [General Angular Guidelines](#general-angular-guidelines)
  - [Kendo UI Components](#kendo-ui-components)
  - [Modern Angular (v20+)](#modern-angular-v20)
- [C# / .NET Development](#-c--net-development)
  - [General C# Guidelines](#general-c-guidelines)
  - [Azure Functions (Isolated Worker)](#azure-functions-isolated-worker)
- [How to Use](#-how-to-use)
- [Principles](#-principles)
- [Resources](#-resources)
- [Output Expectations](#-output-expectations)

---

## 📂 Repository Structure

### 🔧 **General Instructions**

#### Git Workflow
- **`git.instructions.md`**  
  Git workflow and commit guidelines:
  - Meaningful commit messages and regular pulls from main
  - Always ask before proceeding with git operations

### 🅰️ **Angular Development**

#### General Angular Guidelines  
- **`general.instructions.md`**  
  Core rules and conventions for all Angular development in this project:
  - Follow Angular version from `package.json`  
  - Standalone components, signals, new control flow (`@if/@for/@switch`)  
  - SOLID principles, naming conventions, and strict TypeScript usage  
  - RxJS best practices and observable handling  
  - ESLint + Prettier compliance  
  - Respecting existing project structure  

#### Kendo UI Components
- **`kendo.instructions.md`**  
  Specific guidelines for **Kendo UI component usage**:
  - Typed + performant `KendoGrid` setup (client & server ops)  
  - Naming, DRY, and code quality rules  
  - Tooling compliance (lint + format)  
  - SCSS restrictions (use Kendo themes)  

#### Modern Angular (v20+)
- **`angular.instructions.md`**  
  Persona-based instruction set targeting **Angular v20+** and cutting-edge practices:
  - Signals for state management (`signal`, `computed`, `update`)  
  - Standalone components with OnPush change detection  
  - Modern templates using native control flow  
  - Service patterns with `inject()` and `providedIn: 'root'`  
  - RxJS integration (no manual `subscribe()`, use `toSignal`, `| async`)  
  - Strong typing, clean architecture, performance optimization  

### 🔷 **C# / .NET Development**

#### General C# Guidelines
- **`c-sharp.instructions.md`**  
  Comprehensive C# and .NET development guidelines:
  - Modern C# features (file-scoped namespaces, records, pattern matching)
  - SOLID principles and clean architecture patterns
  - Dependency injection and configuration best practices
  - Async/await patterns with proper cancellation support
  - Performance and memory optimization guidelines
  - Comprehensive error handling and logging strategies

#### Azure Functions (Isolated Worker)
- **`dotnet-8-isolated.instructions.md`**  
  Specialized guidelines for **Azure Functions Isolated Worker** on .NET 8:
  - Cold start optimization and performance considerations
  - Azure SDK integration and Managed Identity usage
  - Function-specific patterns (triggers, bindings, hosting)
  - Observability with OpenTelemetry and structured logging
  - Security best practices for cloud environments  

---

## 🚀 How to Use

1. **Load into Copilot**: Use these instruction files as **system prompts** or reference guidelines when working with AI-assisted code generation.  

2. **Technology-Specific Rules**: Choose the appropriate instruction set for your development context:
   - **Angular Projects**: Combine `general.instructions.md` with either `kendo.instructions.md` or `angular.instructions.md`
   - **C# Projects**: Use `c-sharp.instructions.md` for general .NET development
   - **Azure Functions**: Use `dotnet-8-isolated.instructions.md` for serverless applications
   - **Git Operations**: Reference `git.instructions.md` for version control workflows

3. **Consistency**: Generated code must follow these instructions:
   - **Angular**: No `any` types; prefer `unknown` + narrowing. No `ngClass`/`ngStyle` → use native property bindings.  
   - **C#**: Use nullable reference types, modern language features, and proper async patterns.
   - **General**: No new directories unless explicitly required. Analyzer/linter clean output.  

---

## 🔑 Principles

### **All Technologies**
- **Maintainability**: Small, focused components and services.  
- **Performance**: Optimization appropriate to the platform (signals for Angular, async patterns for .NET).  
- **Clarity**: Explicit naming, no abbreviations, no magic numbers.  
- **Consistency**: Follow official style guides and project conventions.

### **Angular-Specific**
- **Signals**: Use for state management and reactive patterns.
- **OnPush**: Prefer OnPush change detection for performance.
- **Virtualization**: Use for large data sets in grids.

### **C#/.NET-Specific**  
- **Immutability**: Prefer records and readonly collections.
- **Dependency Injection**: Use built-in DI container with proper lifetimes.
- **Async/Await**: Default to async patterns with cancellation support.  

---

## 📖 Resources

### **Angular**
- [Angular Components](https://angular.dev/essentials/components)  
- [Angular Signals](https://angular.dev/essentials/signals)  
- [Angular Templates](https://angular.dev/essentials/templates)  
- [Angular DI](https://angular.dev/essentials/dependency-injection)  
- [Angular Style Guide](https://angular.dev/style-guide)  
- [Kendo UI Docs](https://www.telerik.com/kendo-angular-ui/components/)  

### **C# / .NET**
- [.NET Documentation](https://docs.microsoft.com/en-us/dotnet/)
- [C# Programming Guide](https://docs.microsoft.com/en-us/dotnet/csharp/)
- [Azure Functions Documentation](https://docs.microsoft.com/en-us/azure/azure-functions/)
- [.NET Dependency Injection](https://docs.microsoft.com/en-us/dotnet/core/extensions/dependency-injection)
- [Async Programming Patterns](https://docs.microsoft.com/en-us/dotnet/csharp/async)

---

## ✅ Output Expectations

When using these instruction sets, Copilot should generate code that is:

### **All Technologies**
- **Framework version aligned** (from project configuration files)  
- **Typed, clean, maintainable**  
- **Linter/analyzer compliant**  
- **Respectful of existing project structure**  
- **Production-ready without post-cleanup**  

### **Angular-Specific**
- **Signals and OnPush** for performance
- **Standalone components** with modern template syntax
- **ESLint + Prettier compliant**

### **C#/.NET-Specific**
- **Nullable reference types** enabled and respected
- **Modern C# language features** utilized appropriately  
- **Async/await patterns** with proper cancellation
- **Dependency injection** and configuration patterns  
