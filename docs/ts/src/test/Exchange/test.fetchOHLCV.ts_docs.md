# Documentation: ts/src/test/Exchange/test.fetchOHLCV.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/test.fetchOHLCV.ts`
- **Size**: 1,300 bytes
- **Lines**: 29
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import assert from 'assert';
import { Exchange } from "../../../ccxt";
import testOHLCV from './base/test.ohlcv.js';
import testSharedMethods from './base/test.sharedMethods.js';

async function testFetchOHLCV (exchange: Exchange, skippedProperties: object, symbol: string) {
    const method = 'fetchOHLCV';
    const timeframeKeys = Object.keys (exchange.timeframes);
    assert (timeframeKeys.length, exchange.id + ' ' + method + ' - no timeframes found');
    // prefer 1m timeframe if available, otherwise return the first one
    let chosenTimeframeKey = '1m';
    if (!exchange.inArray (chosenTimeframeKey, timeframeKeys)) {
        chosenTimeframeKey = timeframeKeys[0];
    }
    const limit = 10;
    const duration = exchange.parseTimeframe (chosenTimeframeKey);
    const since = exchange.milliseconds () - duration * limit * 1000 - 1000;
    const ohlcvs = await exchange.fetchOHLCV (symbol, chosenTimeframeKey, since, limit);
    testSharedMethods.assertNonEmtpyArray (exchange, skippedProperties, method, ohlcvs, symbol);
    const now = exchange.milliseconds ();
    for (let i = 0; i < ohlcvs.length; i++) {
        testOHLCV (exchange, skippedProperties, method, ohlcvs[i], symbol, now);
    }
    // todo: sorted timestamps check
    return true;
}

export default testFetchOHLCV;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/test.fetchOHLCV.ts`.

**Functions defined**: testFetchOHLCV

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 24
- Comment lines: 2
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFetchOHLCV()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.ohlcv.js` (imported)
- `./base/test.sharedMethods.js` (imported)
- `../../../ccxt` (imported)
- `assert` (imported)
- `./base/test.ohlcv.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/test.fetchOHLCV.ts
```

