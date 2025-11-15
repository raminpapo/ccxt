# Documentation: ts/src/test/Exchange/base/test.marginModification.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/base/test.marginModification.ts`
- **Size**: 1,371 bytes
- **Lines**: 26
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Exchange } from "../../../../ccxt";
import testSharedMethods from './test.sharedMethods.js';

function testMarginModification (exchange: Exchange, skippedProperties: object, method: string, entry: object) {
    const format = {
        'info': {}, // or []
        'type': 'add',
        'amount': exchange.parseNumber ('0.1'),
        'total': exchange.parseNumber ('0.29934828'),
        'code': 'USDT',
        'symbol': 'ADA/USDT:USDT',
        'status': 'ok',
    };
    const emptyAllowedFor = [ 'status', 'symbol', 'code', 'total', 'amount' ];
    testSharedMethods.assertStructure (exchange, skippedProperties, method, entry, format, emptyAllowedFor);
    testSharedMethods.assertCurrencyCode (exchange, skippedProperties, method, entry, entry['code']);
    //
    testSharedMethods.assertGreaterOrEqual (exchange, skippedProperties, method, entry, 'amount', '0');
    testSharedMethods.assertGreaterOrEqual (exchange, skippedProperties, method, entry, 'total', '0');
    testSharedMethods.assertInArray (exchange, skippedProperties, method, entry, 'type', [ 'add', 'reduce', 'set' ]);
    testSharedMethods.assertInArray (exchange, skippedProperties, method, entry, 'status', [ 'ok', 'pending', 'canceled', 'failed' ]);
    testSharedMethods.assertSymbol (exchange, skippedProperties, method, entry, 'symbol');
}

export default testMarginModification;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/base/test.marginModification.ts`.

**Functions defined**: testMarginModification

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 22
- Comment lines: 1
- Blank lines: 3

### Main Components

**Functions** (1):
- `testMarginModification()`



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
npm test ts/src/test/Exchange/base/test.marginModification.ts
```

