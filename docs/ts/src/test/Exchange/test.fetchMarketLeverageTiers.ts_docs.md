# Documentation: ts/src/test/Exchange/test.fetchMarketLeverageTiers.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/test.fetchMarketLeverageTiers.ts`
- **Size**: 705 bytes
- **Lines**: 17
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import assert from 'assert';
import { Exchange } from "../../../ccxt";
import testLeverageTier from './base/test.leverageTier.js';
import testSharedMethods from './base/test.sharedMethods.js';

async function testFetchMarketLeverageTiers (exchange: Exchange, skippedProperties: object, symbol: string) {
    const method = 'fetchMarketLeverageTiers';
    const tiers = await exchange.fetchMarketLeverageTiers (symbol);
    testSharedMethods.assertNonEmtpyArray (exchange, skippedProperties, method, tiers, symbol);
    for (let j = 0; j < tiers.length; j++) {
        testLeverageTier (exchange, skippedProperties, method, tiers[j]);
    }
    return true;
}

export default testFetchMarketLeverageTiers;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/test.fetchMarketLeverageTiers.ts`.

**Functions defined**: testFetchMarketLeverageTiers

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 14
- Comment lines: 0
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFetchMarketLeverageTiers()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.leverageTier.js` (imported)
- `./base/test.sharedMethods.js` (imported)
- `../../../ccxt` (imported)
- `assert` (imported)
- `./base/test.leverageTier.js` (referenced)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/test.fetchMarketLeverageTiers.ts
```

