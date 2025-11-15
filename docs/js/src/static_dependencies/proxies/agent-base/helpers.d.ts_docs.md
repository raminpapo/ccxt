# Documentation: js/src/static_dependencies/proxies/agent-base/helpers.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/proxies/agent-base/helpers.d.ts`
- **Size**: 595 bytes
- **Lines**: 15
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/// <reference types="node" />
/// <reference types="node" />
/// <reference types="node" />
/// <reference types="node" />
/// <reference types="node" />
import * as http from 'http';
import * as https from 'https';
import type { Readable } from 'stream';
export declare type ThenableRequest = http.ClientRequest & {
    then: Promise<http.IncomingMessage>['then'];
};
export declare function toBuffer(stream: Readable): Promise<Buffer>;
export declare function json(stream: Readable): Promise<any>;
export declare function req(url: string | URL, opts?: https.RequestOptions): ThenableRequest;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/proxies/agent-base/helpers.d.ts`.

**Functions defined**: toBuffer, json, req

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 15
- Code lines: 9
- Comment lines: 5
- Blank lines: 1

### Main Components

**Functions** (3):
- `json()`
- `req()`
- `toBuffer()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `https` (imported)
- `http` (imported)
- `stream` (imported)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/proxies/agent-base/helpers.d.ts
```

