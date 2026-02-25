# Backend -- Azure Functions (.NET 8 Isolated)

## Overview

Serverless backend built using Azure Functions (.NET 8 isolated worker
model).

Design principles:

-   DRY
-   SOLID
-   Explicit contracts
-   Dependency Injection
-   Observability and fault tolerance

------------------------------------------------------------------------

## Tech Stack

-   .NET 8
-   Azure Functions Isolated
-   Dependency Injection
-   System.Text.Json
-   Structured logging (ILogger)

------------------------------------------------------------------------

## Architecture

    src/
     ├── Functions/
     ├── Services/
     ├── Domain/
     ├── Infrastructure/
     ├── Models/

------------------------------------------------------------------------

## Design Rules

-   Functions are thin entry points.
-   Services contain business logic.
-   Domain layer is pure.
-   No static mutable state.
-   All dependencies injected.

------------------------------------------------------------------------

## Local Development

``` bash
dotnet restore
func start
```

------------------------------------------------------------------------

## Definition of Done

-   Input validation implemented
-   CancellationToken respected
-   Structured logs
-   No hidden global state
-   Idempotency evaluated
