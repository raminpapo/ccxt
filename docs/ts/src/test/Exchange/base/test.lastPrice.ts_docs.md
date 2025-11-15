# Documentation: ts/src/test/Exchange/base/test.lastPrice.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/base/test.lastPrice.ts`
- **Size**: 1,167 bytes
- **Lines**: 23
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Exchange } from "../../../../ccxt";
import { LastPrice } from "../../../base/types";
import testSharedMethods from './test.sharedMethods.js';

function testLastPrice (exchange: Exchange, skippedProperties: object, method: string, entry: LastPrice, symbol: string) {
    const format = {
        'info': {},
        'symbol': 'ETH/BTC',
        'timestamp': 1502962946216,
        'datetime': '2017-09-01T00:00:00',
        'price': exchange.parseNumber ('1.234'), // price of last trade (closing price for current period)
        'side': 'buy', // buy or sell
    };
    const emptyAllowedFor = [ 'timestamp', 'datetime', 'side', 'price' ]; // binance sometimes provides empty prices for old pairs
    testSharedMethods.assertStructure (exchange, skippedProperties, method, entry, format, emptyAllowedFor);
    testSharedMethods.assertTimestampAndDatetime (exchange, skippedProperties, method, entry);
    //
    testSharedMethods.assertGreater (exchange, skippedProperties, method, entry, 'price', '0');
    testSharedMethods.assertInArray (exchange, skippedProperties, method, entry, 'side', [ 'buy', 'sell', undefined ]);
}

export default testLastPrice;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/base/test.lastPrice.ts`.

**Functions defined**: testLastPrice

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 19
- Comment lines: 1
- Blank lines: 3

### Main Components

**Functions** (1):
- `testLastPrice()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../../base/types` (imported)
- `./test.sharedMethods.js` (imported)
- `../../../../ccxt` (imported)
- `./test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/base/test.lastPrice.ts
```

