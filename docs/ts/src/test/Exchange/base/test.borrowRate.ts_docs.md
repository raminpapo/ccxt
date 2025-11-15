# Documentation: ts/src/test/Exchange/base/test.borrowRate.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/base/test.borrowRate.ts`
- **Size**: 1,221 bytes
- **Lines**: 23
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Exchange } from "../../../../ccxt";
import testSharedMethods from './test.sharedMethods.js';

function testBorrowRate (exchange: Exchange, skippedProperties: object, method: string, entry: object, requestedCode: string) {
    const format = {
        'info': {}, // Or []
        'currency': 'USDT',
        'timestamp': 1638230400000,
        'datetime': '2021-11-30T00:00:00.000Z',
        'rate': exchange.parseNumber ('0.0006'), // Interest rate
        'period': 86400000, // Amount of time the interest rate is based on in milliseconds
    };
    testSharedMethods.assertStructure (exchange, skippedProperties, method, entry, format);
    testSharedMethods.assertTimestampAndDatetime (exchange, skippedProperties, method, entry);
    testSharedMethods.assertCurrencyCode (exchange, skippedProperties, method, entry, entry['currency'], requestedCode);
    //
    // assert (borrowRate['period'] === 86400000 || borrowRate['period'] === 3600000) // Milliseconds in an hour or a day
    testSharedMethods.assertGreater (exchange, skippedProperties, method, entry, 'period', '0');
    testSharedMethods.assertGreater (exchange, skippedProperties, method, entry, 'rate', '0');
}

export default testBorrowRate;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/base/test.borrowRate.ts`.

**Functions defined**: testBorrowRate

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 18
- Comment lines: 2
- Blank lines: 3

### Main Components

**Functions** (1):
- `testBorrowRate()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./test.sharedMethods.js` (imported)
- `../../../../ccxt` (imported)
- `./test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/base/test.borrowRate.ts
```

