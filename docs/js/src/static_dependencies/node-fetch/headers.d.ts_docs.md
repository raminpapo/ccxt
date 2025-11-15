# Documentation: js/src/static_dependencies/node-fetch/headers.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/node-fetch/headers.d.ts`
- **Size**: 1,789 bytes
- **Lines**: 43
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/**
 * Create a Headers object from an http.IncomingMessage.rawHeaders, ignoring those that do
 * not conform to HTTP grammar productions.
 * @param {import('http').IncomingMessage['rawHeaders']} headers
 */
export function fromRawHeaders(headers?: import('http').IncomingMessage['rawHeaders']): Headers;
/**
 * @typedef {Headers | Record<string, string> | Iterable<readonly [string, string]> | Iterable<Iterable<string>>} HeadersInit
 */
/**
 * This Fetch API interface allows you to perform various actions on HTTP request and response headers.
 * These actions include retrieving, setting, adding to, and removing.
 * A Headers object has an associated header list, which is initially empty and consists of zero or more name and value pairs.
 * You can add to this using methods like append() (see Examples.)
 * In all methods of this interface, header names are matched by case-insensitive byte sequence.
 *
 */
export default class Headers extends URLSearchParams {
    /**
     * Headers class
     *
     * @constructor
     * @param {HeadersInit} [init] - Response headers
     */
    constructor(init?: HeadersInit);
    get(name: any): string;
    forEach(callback: any, thisArg?: any): void;
    values(): Generator<string, void, unknown>;
    /**
     * @type {() => IterableIterator<[string, string]>}
     */
    entries(): IterableIterator<[string, string]>;
    /**
     * Node-fetch non-spec method
     * returning all headers and their values as array
     * @returns {Record<string, string[]>}
     */
    raw(): Record<string, string[]>;
    get [Symbol.toStringTag](): string;
    [Symbol.iterator](): IterableIterator<[string, string]>;
}
export type HeadersInit = Headers | Record<string, string> | Iterable<readonly [string, string]> | Iterable<Iterable<string>>;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/node-fetch/headers.d.ts`.

**Classes defined**: Headers

**Functions defined**: fromRawHeaders

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 43
- Code lines: 42
- Comment lines: 30
- Blank lines: -29

### Main Components

**Functions** (1):
- `fromRawHeaders()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/node-fetch/headers.d.ts
```

