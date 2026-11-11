# json-api-builder-create-endpoints

Create resource and file-sync endpoints stage extracted from the existing `json-api-builder` V9 implementation.

## Source

The implementation is located at `src/v1/index.js`. It is copied/extracted from the existing V7/V9 implementation without redesigning its logic.

## Install

```bash
npm install json-api-builder-create-endpoints
```

## Use

```js
import { createEndpoints, createFileSyncEndpoint } from "json-api-builder-create-endpoints";
```

Pass the same options/configuration object used by the original V9 stage.

## Development

```bash
npm install
npm test
npm run check
npm pack --dry-run
```

## Publish

```bash
npm login
npm publish --access public
```

This package is prepared locally only. It has not been published to npm or pushed to GitHub.

