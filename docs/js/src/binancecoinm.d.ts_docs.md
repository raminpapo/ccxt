# Documentation: js/src/binancecoinm.d.ts

## File Metadata

- **Path**: `js/src/binancecoinm.d.ts`
- **Size**: 324 bytes
- **Lines**: 7
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import binance from './binance.js';
export default class binancecoinm extends binance {
    describe(): any;
    transferIn(code: string, amount: any, params?: {}): Promise<import("./base/types.js").TransferEntry>;
    transferOut(code: string, amount: any, params?: {}): Promise<import("./base/types.js").TransferEntry>;
}

```

## High-Level Overview

This is a TypeScript file located at `js/src/binancecoinm.d.ts`.

**Classes defined**: binancecoinm

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 7
- Code lines: 6
- Comment lines: 0
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./binance.js` (imported)
- `./base/types.js` (referenced)
- `./binance.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/binancecoinm.d.ts
```

