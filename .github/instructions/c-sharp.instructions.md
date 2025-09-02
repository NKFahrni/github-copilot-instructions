# General Guidelines (C# / .NET)
- Detect and honor the **.NET target** and **C# language version** from the project’s `.csproj` (`<TargetFramework>`, `<LangVersion>`). Use only APIs available for that target.
- Prefer **immutable, explicit, and typed** designs. Enable and respect **nullable reference types**.
- Use **file-scoped namespaces**, **primary constructors** (when available), modern **pattern matching**, and **switch expressions**.
- Prefer **composition over inheritance**; keep classes focused and small.

# SOLID, Naming & Code Quality
- Apply **SOLID** principles in design and refactors.
- **Naming** (company conventions):
  - Constants: `SCREAMING_SNAKE_CASE` (e.g., `DEFAULT_PAGE_SIZE`).
  - Variables & functions/methods: `camelCase`.
  - Types (classes/records/structs/interfaces/enums): `PascalCase`.
- **No abbreviations** anywhere (avoid `cfg`, `btn`, `usr`; use full words).
- **No magic numbers/strings**: extract to named `const` or `static readonly` fields in the same file or a local constants module.
- **DRY**: after the **second–third** repetition, refactor to a shared function/utility.
- Prefer **small, pure functions** with explicit parameter/return types and clear side-effect boundaries.

# Output Format
- Generate complete, ready-to-paste files with **correct paths** under the **existing folder structure** (do not introduce new folders or move files).
- **Do not create tests**: never generate or fill `*.Tests` projects or test files.
- Include necessary `using` directives; prefer **implicit usings** if the project enables them.

# Project Context
- Language: **C#** (strict, per `<LangVersion>`). Avoid `dynamic` and untyped objects; use `object`/`unknown` equivalent patterns with precise casts.
- Runtime: **.NET** per `<TargetFramework>`; select libraries/APIs accordingly (e.g., `net8.0`, `net6.0`).
- DI & Host: prefer **`Microsoft.Extensions.DependencyInjection`** and the **Generic Host** (`Host.CreateDefaultBuilder` or minimal hosting in ASP.NET Core).

# Language & Tooling Rules
- Output must be **analyzer-clean**: respect project analyzers (Roslyn/IDE, **StyleCop.Analyzers** if present) and **.editorconfig**.
- Always format with **dotnet-format/EditorConfig** conventions (indentation, newlines, ordering).
- Do **not** disable rules with `#pragma warning disable` or `SuppressMessage` unless explicitly requested.

# Async, I/O & Streams
- Default to **async/await** with **`Task`/`ValueTask`** and **`CancellationToken`** parameters for public async APIs.
- In libraries, use `ConfigureAwait(false)` on awaits that do not require the context.
- For streaming results, prefer **`IAsyncEnumerable<T>`** and `await foreach` when appropriate.
- Avoid blocking calls (`.Result`, `.Wait()`). Use timeouts and cancellation cooperatively.

# Collections & Immutability
- Prefer **`IReadOnlyList<T>` / `IReadOnlyDictionary<TKey,TValue>`** for outputs.
- Favor **records** for DTOs/value-like types; use **`init`** setters for controlled mutation.
- Use **`Span<T>`/`Memory<T>`** only when performance-critical and safe for the target.

# Exceptions & Errors
- Use exceptions for exceptional paths only; avoid silent catches.
- Prefer precise exception types; include contextual data in messages.
- Validate inputs at boundaries; return `OneOf`/result types or `Try*` patterns where appropriate.

# Logging & Telemetry
- Inject **`ILogger<T>`**; avoid static loggers.
- Log structured data (named properties), not concatenated strings.

# Configuration & Options
- Bind settings via `IOptions<T>` / `IOptionsMonitor<T>` with validated **options classes**.
- Keep config keys and types strongly typed; avoid magical string keys.

# API/Layering
- Keep **domain logic** independent of frameworks; inject abstractions at boundaries.
- Separate concerns: **Contracts/DTOs**, **Application/Domain**, **Infrastructure/Adapters**, **Presentation** (Web/API/UI).

# Performance & Memory
- Avoid premature allocation; prefer `foreach` over LINQ in hot paths.
- Use `async` I/O, pooling (e.g., `HttpClientFactory`) and caching where it meaningfully reduces latency.
- Benchmark critical paths before micro-optimizing.

# Source Layout & Files
- One top-level type per file (except very small, closely related types).
- Organize partial classes carefully; avoid scattering logic.
- Keep constants near usage or in a local `Constants` file within the **existing** folder structure.
