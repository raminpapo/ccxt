# Documentation: js/src/base/functions/number.d.ts

## File Metadata

- **Path**: `js/src/base/functions/number.d.ts`
- **Size**: 1,269 bytes
- **Lines**: 28
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
declare const TRUNCATE = 0;
declare const ROUND = 1;
declare const ROUND_UP = 2;
declare const ROUND_DOWN = 3;
declare const DECIMAL_PLACES = 2;
declare const SIGNIFICANT_DIGITS = 3;
declare const TICK_SIZE = 4;
declare const NO_PADDING = 5;
declare const PAD_WITH_ZERO = 6;
declare const precisionConstants: {
    ROUND: number;
    TRUNCATE: number;
    ROUND_UP: number;
    ROUND_DOWN: number;
    DECIMAL_PLACES: number;
    SIGNIFICANT_DIGITS: number;
    TICK_SIZE: number;
    NO_PADDING: number;
    PAD_WITH_ZERO: number;
};
declare function numberToString(x: any): string | undefined;
declare const truncate_to_string: (num: number | string, precision?: number) => string;
declare const truncate: (num: number | string, precision?: number) => number;
declare function precisionFromString(str: string): number;
declare const decimalToPrecision: (x: string, roundingMode: number, numPrecisionDigits: any, countingMode?: number, paddingMode?: number) => string;
declare function omitZero(stringNumber: string): string;
export { numberToString, precisionFromString, decimalToPrecision, truncate_to_string, truncate, omitZero, precisionConstants, ROUND, TRUNCATE, ROUND_UP, ROUND_DOWN, DECIMAL_PLACES, SIGNIFICANT_DIGITS, TICK_SIZE, NO_PADDING, PAD_WITH_ZERO, };

```

## High-Level Overview

This is a TypeScript file located at `js/src/base/functions/number.d.ts`.

**Functions defined**: numberToString, precisionFromString, omitZero



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 27
- Comment lines: 0
- Blank lines: 1

### Main Components

**Functions** (3):
- `numberToString()`
- `omitZero()`
- `precisionFromString()`

**Constants** (9):
- `DECIMAL_PLACES`
- `NO_PADDING`
- `PAD_WITH_ZERO`
- `ROUND`
- `ROUND_DOWN`
- `ROUND_UP`
- `SIGNIFICANT_DIGITS`
- `TICK_SIZE`
- `TRUNCATE`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/base/functions/number.d.ts
```

