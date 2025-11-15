# Documentation: ts/src/test/Exchange/test.fetchFundingRateHistory.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/test.fetchFundingRateHistory.ts`
- **Size**: 875 bytes
- **Lines**: 18
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import assert from 'assert';
import { Exchange } from "../../../ccxt";
import testFundingRateHistory from './base/test.fundingRateHistory.js';
import testSharedMethods from './base/test.sharedMethods.js';

async function testFetchFundingRateHistory (exchange: Exchange, skippedProperties: object, symbol: string) {
    const method = 'fetchFundingRateHistory';
    const fundingRatesHistory = await exchange.fetchFundingRateHistory (symbol);
    testSharedMethods.assertNonEmtpyArray (exchange, skippedProperties, method, fundingRatesHistory, symbol);
    for (let i = 0; i < fundingRatesHistory.length; i++) {
        testFundingRateHistory (exchange, skippedProperties, method, fundingRatesHistory[i], symbol);
    }
    testSharedMethods.assertTimestampOrder (exchange, method, symbol, fundingRatesHistory);
    return true;
}

export default testFetchFundingRateHistory;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/test.fetchFundingRateHistory.ts`.

**Functions defined**: testFetchFundingRateHistory

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 18
- Code lines: 15
- Comment lines: 0
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFetchFundingRateHistory()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.sharedMethods.js` (imported)
- `../../../ccxt` (imported)
- `./base/test.fundingRateHistory.js` (imported)
- `assert` (imported)
- `./base/test.fundingRateHistory.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/test.fetchFundingRateHistory.ts
```

