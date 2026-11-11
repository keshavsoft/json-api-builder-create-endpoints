# json-api-builder-create-endpoints

[![npm version](https://img.shields.io/npm/v/json-api-builder-create-endpoints?color=cb3837&style=flat-square)](https://www.npmjs.com/package/json-api-builder-create-endpoints)
[![license: MIT](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](LICENSE)
[![Node.js](https://img.shields.io/badge/node-%3E%3D20-brightgreen.svg?style=flat-square)](package.json)
[![GitHub Repository](https://img.shields.io/badge/GitHub-keshavsoft%2Fjson-api-builder-create-endpoints-181717.svg?style=flat-square&logo=github)](https://github.com/keshavsoft/json-api-builder-create-endpoints)
[![Documentation](https://img.shields.io/badge/docs-live_portal-amber.svg?style=flat-square)](https://keshavsoft.github.io/json-api-builder-create-endpoints/)

> **Stage 6 of 8**: Stage 6: REST Endpoints & Local JSON File-Sync Handlers

Part of the modular **[JSON API Builder](https://github.com/keshavsoft/json-api-builder-orchestrator)** ecosystem by [KeshavSoft](https://github.com/keshavsoft).

---

## The Story

Generates resource endpoints and file-sync handlers (/fs/...) that expose safe JSON read/write persistence for client data models (e.g., clinics.json, players.json).

### The Problem It Solves
Front-end and prototype developers need instant, reliable read/write REST endpoints for their local JSON fixtures without setting up heavy database containers.

### The Solution
Generates dedicated /fs file-sync endpoints and resource routers that read, validate, and write back to local JSON data stores with standard HTTP GET, POST, PUT, DELETE methods.

---

## Architecture & Pipeline Position

```
[1. Folders] ──▶ [2. Files] ──▶ [3. Content] ──▶ [4. Hook Routes]
                                                         │
[8. Orchestrator] ◀── [7. Validate] ◀── [6. Endpoints] ◀── [5. App]
```

**This repository implements Stage 6 in isolation.** It can be used independently in custom build workflows or composed automatically via `json-api-builder`.

---

## Installation

```bash
npm install json-api-builder-create-endpoints
```

---

## Quick Start

```js
import { createEndpoints, createFileSyncEndpoint } from "json-api-builder-create-endpoints";

createFileSyncEndpoint({ clientRoot: "./my-project", outputRoot: "./my-project/output" });
createEndpoints({ clientRoot: "./my-project", outputRoot: "./my-project/output" });
```

---

## Input Specification

JSON model files that represent entity data stores.

```json
input/data/
├── clinics.json
└── players.json
```

---

## Output Transformation

Active HTTP route handlers exposing CRUD operations over JSON fixtures.

```text
// GET /fs/clinics -> returns clinics.json
// POST /fs/clinics -> appends new clinic record
// PUT /fs/clinics/:id -> updates clinic record
// DELETE /fs/clinics/:id -> removes clinic record
```

---

## API Reference

### `createEndpoints`, `createFileSyncEndpoint`

Accepts an options object with the following configuration:

| Option | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `clientRoot` | `string` | `process.cwd()` | Root path of the client project. |
| `outputRoot` | `string` | `path.join(clientRoot, 'output')` | Target output directory. |
| `dataPath` | `string` | `input/data` | Location of JSON data fixture files. |

---

## Sibling Pipeline Packages

| Stage | Package | Description |
| :---: | :--- | :--- |
| **01** | [json-api-builder-create-folders](https://github.com/keshavsoft/json-api-builder-create-folders) | Directory hierarchy scaffolding |
| **02** | [json-api-builder-create-files](https://github.com/keshavsoft/json-api-builder-create-files) | Non-destructive placeholder file creation |
| **03** | [json-api-builder-insert-content](https://github.com/keshavsoft/json-api-builder-insert-content) | ESTree template to JavaScript insertion |
| **04** | [json-api-builder-alter-content](https://github.com/keshavsoft/json-api-builder-alter-content) | Hierarchical route hooking & AST imports |
| **05** | [json-api-builder-create-app](https://github.com/keshavsoft/json-api-builder-create-app) | Root app.js assembly & server runtime |
| **06** | [json-api-builder-create-endpoints](https://github.com/keshavsoft/json-api-builder-create-endpoints) | CRUD endpoints & local JSON file sync |
| **07** | [json-api-builder-validation](https://github.com/keshavsoft/json-api-builder-validation) | Specification linting & artifact checks |
| **08** | [json-api-builder](https://github.com/keshavsoft/json-api-builder-orchestrator) | Master orchestrator coordinating all stages |

---

## Development & Testing

```bash
# Install dependencies
npm install

# Run automated tests
npm test

# Run syntax check
npm run check

# Prepublish verification
npm run prepublishOnly
```

---

## License

[MIT](LICENSE) © 2026 [KeshavSoft](https://github.com/keshavsoft)
