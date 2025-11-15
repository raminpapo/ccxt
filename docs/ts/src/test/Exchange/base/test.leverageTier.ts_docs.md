# Documentation: ts/src/test/Exchange/base/test.leverageTier.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/base/test.leverageTier.ts`
- **Size**: 1,277 bytes
- **Lines**: 24
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Exchange } from "../../../../ccxt";
import testSharedMethods from './test.sharedMethods.js';

function testLeverageTier (exchange: Exchange, skippedProperties: object, method: string, entry: object) {
    const format = {
        'tier': exchange.parseNumber ('1'),
        'minNotional': exchange.parseNumber ('0'),
        'maxNotional': exchange.parseNumber ('5000'),
        'maintenanceMarginRate': exchange.parseNumber ('0.01'),
        'maxLeverage': exchange.parseNumber ('25'),
        'info': {},
    };
    const emptyAllowedFor = [ 'maintenanceMarginRate' ];
    testSharedMethods.assertStructure (exchange, skippedProperties, method, entry, format, emptyAllowedFor);
    //
    testSharedMethods.assertGreaterOrEqual (exchange, skippedProperties, method, entry, 'tier', '0');
    testSharedMethods.assertGreaterOrEqual (exchange, skippedProperties, method, entry, 'minNotional', '0');
    testSharedMethods.assertGreaterOrEqual (exchange, skippedProperties, method, entry, 'maxNotional', '0');
    testSharedMethods.assertGreaterOrEqual (exchange, skippedProperties, method, entry, 'maxLeverage', '1');
    testSharedMethods.assertLessOrEqual (exchange, skippedProperties, method, entry, 'maintenanceMarginRate', '1');
}

export default testLeverageTier;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/base/test.leverageTier.ts`.

**Functions defined**: testLeverageTier

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 24
- Code lines: 20
- Comment lines: 1
- Blank lines: 3

### Main Components

**Functions** (1):
- `testLeverageTier()`



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
npm test ts/src/test/Exchange/base/test.leverageTier.ts
```

