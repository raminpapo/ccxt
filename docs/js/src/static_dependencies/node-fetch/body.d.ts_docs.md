# Documentation: js/src/static_dependencies/node-fetch/body.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/node-fetch/body.d.ts`
- **Size**: 1,438 bytes
- **Lines**: 62
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/// <reference types="node" />
/// <reference types="node" />
/**
 * Body mixin
 *
 * Ref: https://fetch.spec.whatwg.org/#body
 *
 * @param   Stream  body  Readable stream
 * @param   Object  opts  Response options
 * @return  Void
 */
export default class Body {
    constructor(body: any, { size }?: {
        size?: number;
    });
    size: number;
    get body(): any;
    get bodyUsed(): boolean;
    /**
     * Decode response as ArrayBuffer
     *
     * @return  Promise
     */
    arrayBuffer(): Promise<ArrayBuffer>;
    /**
     * Return raw response as Blob
     *
     * @return Promise
     */
    blob(): Promise<Blob>;
    /**
     * Decode response as json
     *
     * @return  Promise
     */
    json(): Promise<any>;
    /**
     * Decode response as text
     *
     * @return  Promise
     */
    text(): Promise<string>;
    buffer: () => Promise<Buffer>;
    [INTERNALS]: {
        body: any;
        stream: any;
        boundary: any;
        disturbed: boolean;
        error: any;
    };
}
export function clone(instance: any, highWaterMark: any): any;
export function extractContentType(body: any, request: any): string | null;
export function getTotalBytes(request: any): number | null;
export function writeToStream(dest: Stream.Writable, { body }: {
    body: any;
}): Promise<void>;
import { Buffer } from "buffer";
declare const INTERNALS: unique symbol;
import Stream from "node:stream";
export {};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/node-fetch/body.d.ts`.

**Classes defined**: Body

**Functions defined**: clone, writeToStream, extractContentType, getTotalBytes

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 62
- Code lines: 59
- Comment lines: 31
- Blank lines: -28

### Main Components

**Classes** (1):
- `Body`

**Functions** (4):
- `clone()`
- `extractContentType()`
- `getTotalBytes()`
- `writeToStream()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `buffer` (imported)
- `node:stream` (imported)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/node-fetch/body.d.ts
```

