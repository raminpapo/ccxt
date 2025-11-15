# Documentation: ts/src/test/Exchange/base/test.borrowInterest.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/base/test.borrowInterest.ts`
- **Size**: 1,447 bytes
- **Lines**: 26
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Exchange } from "../../../../ccxt";
import testSharedMethods from './test.sharedMethods.js';

function testBorrowInterest (exchange: Exchange, skippedProperties: object, method: string, entry: object, requestedCode: string, requestedSymbol: string) {
    const format = {
        'info': {},
        'account': 'BTC/USDT',
        'currency': 'USDT',
        'interest': exchange.parseNumber ('0.1444'),
        'interestRate': exchange.parseNumber ('0.0006'),
        'amountBorrowed': exchange.parseNumber ('30.0'),
        'timestamp': 1638230400000,
        'datetime': '2021-11-30T00:00:00.000Z',
    };
    const emptyAllowedFor = [ 'account' ];
    testSharedMethods.assertStructure (exchange, skippedProperties, method, entry, format, emptyAllowedFor);
    testSharedMethods.assertTimestampAndDatetime (exchange, skippedProperties, method, entry);
    testSharedMethods.assertCurrencyCode (exchange, skippedProperties, method, entry, entry['currency'], requestedCode);
    testSharedMethods.assertSymbol (exchange, skippedProperties, method, entry, entry['account'], requestedSymbol);
    testSharedMethods.assertGreater (exchange, skippedProperties, method, entry, 'interest', '0');
    testSharedMethods.assertGreater (exchange, skippedProperties, method, entry, 'interestRate', '0');
    testSharedMethods.assertGreater (exchange, skippedProperties, method, entry, 'amountBorrowed', '0');
}

export default testBorrowInterest;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/base/test.borrowInterest.ts`.

**Functions defined**: testBorrowInterest

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 23
- Comment lines: 0
- Blank lines: 3

### Main Components

**Functions** (1):
- `testBorrowInterest()`



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
npm test ts/src/test/Exchange/base/test.borrowInterest.ts
```

