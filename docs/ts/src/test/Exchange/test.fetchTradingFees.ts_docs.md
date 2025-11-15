# Documentation: ts/src/test/Exchange/test.fetchTradingFees.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/test.fetchTradingFees.ts`
- **Size**: 698 bytes
- **Lines**: 18
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Exchange } from "../../../ccxt";
import testTradingFee from './base/test.tradingFee.js';
import testSharedMethods from './base/test.sharedMethods.js';

async function testFetchTradingFees (exchange: Exchange, skippedProperties: object) {
    const method = 'fetchTradingFees';
    const fees = await exchange.fetchTradingFees ();
    const symbols = Object.keys (fees);
    testSharedMethods.assertNonEmtpyArray (exchange, skippedProperties, method, symbols);
    for (let i = 0; i < symbols.length; i++) {
        const symbol = symbols[i];
        testTradingFee (exchange, skippedProperties, method, symbol, fees[symbol]);
    }
    return true;
}

export default testFetchTradingFees;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/test.fetchTradingFees.ts`.

**Functions defined**: testFetchTradingFees

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 18
- Code lines: 15
- Comment lines: 0
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFetchTradingFees()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.sharedMethods.js` (imported)
- `./base/test.tradingFee.js` (imported)
- `../../../ccxt` (imported)
- `./base/test.tradingFee.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/test.fetchTradingFees.ts
```

