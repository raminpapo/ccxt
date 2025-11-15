# Documentation: js/src/static_dependencies/ethers/utils/units.d.ts

## File Metadata

- **Path**: `js/src/static_dependencies/ethers/utils/units.d.ts`
- **Size**: 971 bytes
- **Lines**: 24
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import type { BigNumberish, Numeric } from "../utils/index.js";
/**
 *  Converts %%value%% into a //decimal string//, assuming %%unit%% decimal
 *  places. The %%unit%% may be the number of decimal places or the name of
 *  a unit (e.g. ``"gwei"`` for 9 decimal places).
 *
 */
export declare function formatUnits(value: BigNumberish, unit?: string | Numeric): string;
/**
 *  Converts the //decimal string// %%value%% to a BigInt, assuming
 *  %%unit%% decimal places. The %%unit%% may the number of decimal places
 *  or the name of a unit (e.g. ``"gwei"`` for 9 decimal places).
 */
export declare function parseUnits(value: string, unit?: string | Numeric): bigint;
/**
 *  Converts %%value%% into a //decimal string// using 18 decimal places.
 */
export declare function formatEther(wei: BigNumberish): string;
/**
 *  Converts the //decimal string// %%ether%% to a BigInt, using 18
 *  decimal places.
 */
export declare function parseEther(ether: string): bigint;

```

## High-Level Overview

This is a TypeScript file located at `js/src/static_dependencies/ethers/utils/units.d.ts`.

**Functions defined**: formatEther, parseEther, formatUnits, parseUnits

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 24
- Code lines: 23
- Comment lines: 18
- Blank lines: -17

### Main Components

**Functions** (4):
- `formatEther()`
- `formatUnits()`
- `parseEther()`
- `parseUnits()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../utils/index.js` (imported)
- `../utils/index.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/static_dependencies/ethers/utils/units.d.ts
```

