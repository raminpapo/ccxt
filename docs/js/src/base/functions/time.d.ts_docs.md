# Documentation: js/src/base/functions/time.d.ts

## File Metadata

- **Path**: `js/src/base/functions/time.d.ts`
- **Size**: 1,185 bytes
- **Lines**: 22
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
declare const now: () => number;
declare const microseconds: () => number;
declare const milliseconds: () => number;
declare const seconds: () => number;
declare const uuidv1: () => string;
declare const setTimeout_safe: (done: any, ms: any, setTimeout?: any, targetTime?: any) => () => void;
declare class TimedOut extends Error {
    constructor();
}
declare const iso8601: (timestamp: any) => string;
declare const parse8601: (x: any) => number;
declare const parseDate: (x: any) => number;
declare const rfc2616: (timestamp?: any) => string;
declare const mdy: (timestamp: any, infix?: string) => string;
declare const ymd: (timestamp: any, infix: any, fullYear?: boolean) => string;
declare const yymmdd: (timestamp: any, infix?: string) => string;
declare const yyyymmdd: (timestamp: any, infix?: string) => string;
declare const ymdhms: (timestamp: any, infix?: string) => string;
declare const sleep: (ms: any) => Promise<unknown>;
declare const timeout: (ms: any, promise: any) => Promise<any>;
export { now, microseconds, milliseconds, seconds, iso8601, parse8601, rfc2616, uuidv1, parseDate, mdy, ymd, yymmdd, yyyymmdd, ymdhms, setTimeout_safe, sleep, TimedOut, timeout, };

```

## High-Level Overview

This is a TypeScript file located at `js/src/base/functions/time.d.ts`.

**Classes defined**: TimedOut



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 21
- Comment lines: 0
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/base/functions/time.d.ts
```

