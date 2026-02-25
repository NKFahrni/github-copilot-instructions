# Backend -- AWS Lambda (Node.js + TypeScript)

## Overview

Serverless backend functions running on AWS Lambda using strict
TypeScript.

Architecture principles:

-   DRY
-   SOLID
-   Functional core / Imperative shell
-   Strong typing
-   Minimal dependencies

------------------------------------------------------------------------

## Tech Stack

-   Node.js
-   TypeScript (strict mode)
-   AWS Lambda
-   API Gateway / SQS / EventBridge

------------------------------------------------------------------------

## Architecture

    src/
     ├── handlers/
     ├── services/
     ├── domain/
     ├── infrastructure/
     ├── models/

------------------------------------------------------------------------

## Development

``` bash
npm install
npm run build
npm run local
```

------------------------------------------------------------------------

## Definition of Done

-   Strict TypeScript passes
-   No any types
-   Input validation implemented
-   Retry behaviour evaluated
-   Cold-start impact reasonable
