# Documentation: ts/src/test/Exchange/base/test.fundingRateHistory.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/base/test.fundingRateHistory.ts`
- **Size**: 998 bytes
- **Lines**: 20
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Exchange } from "../../../../ccxt";
import testSharedMethods from './test.sharedMethods.js';

function testFundingRateHistory (exchange: Exchange, skippedProperties: object, method: string, entry: object, symbol: string) {
    const format = {
        'info': {}, // Or []
        'symbol': 'BTC/USDT:USDT',
        'timestamp': 1638230400000,
        'datetime': '2021-11-30T00:00:00.000Z',
        'fundingRate': exchange.parseNumber ('0.0006'),
    };
    testSharedMethods.assertStructure (exchange, skippedProperties, method, entry, format);
    testSharedMethods.assertSymbol (exchange, skippedProperties, method, entry, 'symbol', symbol);
    testSharedMethods.assertTimestampAndDatetime (exchange, skippedProperties, method, entry);
    testSharedMethods.assertGreater (exchange, skippedProperties, method, entry, 'fundingRate', '-100');
    testSharedMethods.assertLess (exchange, skippedProperties, method, entry, 'fundingRate', '100');
}

export default testFundingRateHistory;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/base/test.fundingRateHistory.ts`.

**Functions defined**: testFundingRateHistory

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 20
- Code lines: 17
- Comment lines: 0
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFundingRateHistory()`



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
npm test ts/src/test/Exchange/base/test.fundingRateHistory.ts
```

