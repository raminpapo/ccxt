# Documentation: js/src/static_dependencies/node-fetch/request.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/node-fetch/request.d.ts`
- **Size**: 1,412 bytes
- **Lines**: 61
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
/**
 * Request class
 *
 * Ref: https://fetch.spec.whatwg.org/#request-class
 *
 * @param   Mixed   input  Url or Request instance
 * @param   Object  init   Custom options
 * @return  Void
 */
export default class Request extends Body {
    constructor(input: any, init?: {});
    follow: any;
    compress: any;
    counter: any;
    agent: any;
    highWaterMark: any;
    insecureHTTPParser: any;
    set referrerPolicy(arg: any);
    get referrerPolicy(): any;
    /** @returns {string} */
    get method(): string;
    /** @returns {string} */
    get url(): string;
    /** @returns {Headers} */
    get headers(): Headers;
    get redirect(): any;
    /** @returns {AbortSignal} */
    get signal(): AbortSignal;
    get referrer(): any;
    /**
     * Clone this request
     *
     * @return  Request
     */
    clone(): Request;
    get [Symbol.toStringTag](): string;
    [INTERNALS]: {
        method: any;
        redirect: any;
        headers: Headers;
        parsedURL: URL;
        signal: any;
        referrer: any;
    };
}
export function getNodeRequestOptions(request: Request): {
    /** @type {URL} */
    parsedURL: URL;
    options: {
        path: string;
        method: string;
        headers: any;
        insecureHTTPParser: any;
        agent: any;
    };
};
import Body from "./body.js";
import Headers from "./headers.js";
declare const INTERNALS: unique symbol;
export {};

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/node-fetch/request.d.ts`.

**Classes defined**: Request

**Functions defined**: getNodeRequestOptions

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 61
- Code lines: 60
- Comment lines: 19
- Blank lines: -18

### Main Components

**Functions** (1):
- `getNodeRequestOptions()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./headers.js` (imported)
- `./body.js` (imported)
- `./headers.js` (referenced)
- `./body.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/node-fetch/request.d.ts
```

