# General Guidelines (.NET 8 Azure Functions — Isolated Worker)
- Detect and honor **Target Framework** and **LangVersion** from the project `.csproj` (e.g., `<TargetFramework>net8.0</TargetFramework>`).
- Use **Azure Functions Isolated Worker** APIs (`Microsoft.Azure.Functions.Worker`), not the in-process model.
- Prefer **immutable, explicit, and typed** designs. Enable and respect **nullable reference types**.
- Use **file-scoped namespaces**, modern **pattern matching**, and **switch expressions**.
- Compose via **Dependency Injection**; avoid service locators and static state.
- Logging via **`ILogger<T>`** or `FunctionContext.GetLogger<T>()`. Prefer **structured logging**.
- Configuration via **`IConfiguration`** (environment variables / `appsettings.*.json`). Validate with **DataAnnotations** in options.
- Support **cancellation** on all async entry points with `CancellationToken`.
- Use **Azure SDK** clients via **`AddAzureClients`** (HTTP pipeline, retries, auth) rather than hand-rolled `HttpClient`.

# Performance & Cold Start
- Design for cold start scenarios; avoid heavy initialization in constructors.
- Use static initialization sparingly; prefer lazy initialization or DI.
- Keep function app warm with appropriate hosting plans when needed.

# SOLID, Naming & Code Quality
- Apply **SOLID** principles in design and refactors.
- **Naming**:
   - Constants: `SCREAMING_SNAKE_CASE` (e.g., `DEFAULT_PAGE_SIZE`).
  - Variables & functions/methods: `camelCase`.
  - **Private/protected fields**: `_camelCase` (leading underscore).
  - Types (classes/records/structs/interfaces/enums): `PascalCase`.
- **No abbreviations** (avoid `cfg`, `usr`, `svc`; use full words).
- **No magic numbers/strings**: extract to named `const` or `static readonly` fields (same file or local constants module).
- **DRY**: after the **second–third** repetition, refactor into a shared function/utility.
- Prefer **small, pure functions** with explicit parameter/return types and clear side-effect boundaries.

# Output Format
- Generate complete, ready-to-paste files with **correct paths**.
- **Do not create tests**: never generate or fill any test projects or files.
- Respect the **existing folder structure**; do not invent new folders or move files.

# Project Context
- Runtime: **Azure Functions Isolated Worker** on **.NET 8**.
- Hosting: Minimal host in `Program.cs` with `Host.CreateDefaultBuilder(args).ConfigureFunctionsWorkerDefaults()`.
- Triggers & Bindings: Use **attributes** (e.g., `HttpTrigger`, `TimerTrigger`, `ServiceBusTrigger`, `BlobOutput`).
- DI: Register services/config with `builder.Services` and `builder.Configuration`.
- Telemetry: Prefer **OpenTelemetry** (`AddOpenTelemetry`) with Azure Monitor exporter if present.

# Dependency Injection
- Register dependencies with appropriate lifetimes (Singleton, Scoped, Transient).
- Prefer constructor injection; avoid service locator pattern.
- Use `IOptions<T>` for configuration; validate at startup.

# Language & Tooling Rules
- Must be **analyzer-clean**; respect **.editorconfig**, Roslyn analyzers, and StyleCop (if configured).
- Always format with **dotnet-format/EditorConfig** conventions.
- Do **not** disable rules with pragmas unless explicitly requested.

# Async, I/O & Resilience
- Default to **async/await** with `Task`/`ValueTask` and **propagate `CancellationToken`**.
- Avoid blocking (`.Result`, `.Wait()`).
- Prefer **`IHttpClientFactory`** or **Azure SDK** clients; do not instantiate raw `HttpClient` repeatedly.
- Apply resilience where appropriate (e.g., retry/backoff via Polly or Azure SDK built-ins).

# Bindings & Contracts
- Keep **function signatures minimal**: bind inputs to typed parameters (e.g., `HttpRequestData`, POCOs via bindings).
- Return **`HttpResponseData`** for HTTP; for output bindings use attributes (`[BlobOutput]`, `[QueueOutput]`).
- Validate all inputs; return accurate HTTP status codes and problem details for HTTP functions.

# Security & Config
- Never log secrets; load keys from **App Settings/Environment** or Managed Identity.
- Prefer **Managed Identity** over keys when calling Azure resources.
- Validate options at startup; fail fast on invalid configuration.

# Observability
- Log **structured data** (named properties) at appropriate levels.
- Emit **traces/metrics** with OpenTelemetry when configured.

# File Organization
- One function class per file (or a small cohesive set); one top-level type per file.
- Function names should be descriptive and follow PascalCase (e.g., `ProcessOrderQueue`, `HandleWebhook`).
- Keep constants near usage or in a local `Constants` file within the **existing** structure.

