# Documentation: ts/src/test/Exchange/base/test.tradingFee.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/base/test.tradingFee.ts`
- **Size**: 877 bytes
- **Lines**: 20
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Exchange } from "../../../../ccxt";
import testSharedMethods from './test.sharedMethods.js';

function testTradingFee (exchange: Exchange, skippedProperties: object, method: string, symbol: string, entry: object) {
    const format = {
        'info': { },
        'symbol': 'ETH/BTC',
        'maker': exchange.parseNumber ('0.002'),
        'taker': exchange.parseNumber ('0.003'),
        // todo: most exchanges do not have the below props implemented, so comment out it temporarily
        // 'percentage': false,
        // 'tierBased': false,
    };
    const emptyAllowedFor = [ 'tierBased', 'percentage', 'symbol' ];
    testSharedMethods.assertStructure (exchange, skippedProperties, method, entry, format, emptyAllowedFor);
    testSharedMethods.assertSymbol (exchange, skippedProperties, method, entry, 'symbol', symbol);
}

export default testTradingFee;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/base/test.tradingFee.ts`.

**Functions defined**: testTradingFee

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 20
- Code lines: 14
- Comment lines: 3
- Blank lines: 3

### Main Components

**Functions** (1):
- `testTradingFee()`



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
npm test ts/src/test/Exchange/base/test.tradingFee.ts
```

