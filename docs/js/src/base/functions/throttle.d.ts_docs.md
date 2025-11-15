# Documentation: js/src/base/functions/throttle.d.ts

## File Metadata

- **Path**: `js/src/base/functions/throttle.d.ts`
- **Size**: 152 bytes
- **Lines**: 7
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
declare class Throttler {
    constructor(config: any);
    loop(): Promise<void>;
    throttle(cost?: any): Promise<unknown>;
}
export { Throttler, };

```

## High-Level Overview

This is a TypeScript file located at `js/src/base/functions/throttle.d.ts`.

**Classes defined**: Throttler



## Detailed Walkthrough

### Code Structure

- Total lines: 7
- Code lines: 6
- Comment lines: 0
- Blank lines: 1

### Main Components

**Classes** (1):
- `Throttler`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/base/functions/throttle.d.ts
```

