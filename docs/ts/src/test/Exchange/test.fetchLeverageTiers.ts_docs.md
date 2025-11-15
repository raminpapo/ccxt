# Documentation: ts/src/test/Exchange/test.fetchLeverageTiers.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/test.fetchLeverageTiers.ts`
- **Size**: 1,202 bytes
- **Lines**: 28
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import assert from 'assert';
import { Exchange } from "../../../ccxt";
import testLeverageTier from './base/test.leverageTier.js';
import testSharedMethods from './base/test.sharedMethods.js';

async function testFetchLeverageTiers (exchange: Exchange, skippedProperties: object, symbol: string) {
    const method = 'fetchLeverageTiers';
    const tiers = await exchange.fetchLeverageTiers ([ 'symbol' ]);
    // const format = {
    //     'RAY/USDT': [
    //       {},
    //     ],
    // };
    assert (typeof tiers === 'object', exchange.id + ' ' + method + ' ' + symbol + ' must return an object. ' + exchange.json (tiers));
    const tierKeys = Object.keys (tiers);
    testSharedMethods.assertNonEmtpyArray (exchange, skippedProperties, method, tierKeys, symbol);
    for (let i = 0; i < tierKeys.length; i++) {
        const tiersForSymbol = tiers[tierKeys[i]];
        testSharedMethods.assertNonEmtpyArray (exchange, skippedProperties, method, tiersForSymbol, symbol);
        for (let j = 0; j < tiersForSymbol.length; j++) {
            testLeverageTier (exchange, skippedProperties, method, tiersForSymbol[j]);
        }
    }
    return true;
}

export default testFetchLeverageTiers;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/test.fetchLeverageTiers.ts`.

**Functions defined**: testFetchLeverageTiers

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 20
- Comment lines: 5
- Blank lines: 3

### Main Components

**Functions** (1):
- `testFetchLeverageTiers()`



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
npm test ts/src/test/Exchange/test.fetchLeverageTiers.ts
```

