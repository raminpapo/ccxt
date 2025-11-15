# Documentation: ts/src/test/Exchange/base/test.openInterest.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/base/test.openInterest.ts`
- **Size**: 1,333 bytes
- **Lines**: 25
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Exchange } from "../../../../ccxt";
import testSharedMethods from './test.sharedMethods.js';

function testOpenInterest (exchange: Exchange, skippedProperties: object, method: string, entry: object) {
    const format = {
        'symbol': 'BTC/USDT',
        // 'baseVolume': exchange.parseNumber ('81094.084'), // deprecated
        // 'quoteVolume': exchange.parseNumber ('3544581864.598'), //deprecated
        'openInterestAmount': exchange.parseNumber ('3544581864.598'),
        'openInterestValue': exchange.parseNumber ('3544581864.598'),
        'timestamp': 1649373600000,
        'datetime': '2022-04-07T23:20:00.000Z',
        'info': {},
    };
    const emptyAllowedFor = [ 'symbol', 'timestamp', 'openInterestAmount', 'openInterestValue', 'datetime' ];
    testSharedMethods.assertStructure (exchange, skippedProperties, method, entry, format, emptyAllowedFor);
    testSharedMethods.assertSymbol (exchange, skippedProperties, method, entry, 'symbol');
    testSharedMethods.assertTimestampAndDatetime (exchange, skippedProperties, method, entry);
    //
    testSharedMethods.assertGreater (exchange, skippedProperties, method, entry, 'openInterestAmount', '0');
    testSharedMethods.assertGreater (exchange, skippedProperties, method, entry, 'openInterestValue', '0');
}

export default testOpenInterest;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/base/test.openInterest.ts`.

**Functions defined**: testOpenInterest

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 19
- Comment lines: 3
- Blank lines: 3

### Main Components

**Functions** (1):
- `testOpenInterest()`



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
npm test ts/src/test/Exchange/base/test.openInterest.ts
```

