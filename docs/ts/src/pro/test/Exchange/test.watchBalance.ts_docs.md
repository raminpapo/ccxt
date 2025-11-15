# Documentation: ts/src/pro/test/Exchange/test.watchBalance.ts

## File Metadata

- **Path**: `ts/src/pro/test/Exchange/test.watchBalance.ts`
- **Size**: 942 bytes
- **Lines**: 31
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

import testBalance from '../../../test/Exchange/base/test.balance.js';
import testSharedMethods from '../../../test/Exchange/base/test.sharedMethods.js';

async function testWatchBalance (exchange, skippedProperties, code) {
    const method = 'watchBalance';
    let now = exchange.milliseconds ();
    const ends = now + 15000;
    while (now < ends) {
        let response = undefined;
        let success = true;
        try {
            response = await exchange.watchBalance ();
        } catch (e) {
            if (!testSharedMethods.isTemporaryFailure (e)) {
                throw e;
            }
            now = exchange.milliseconds ();
            // continue;
            success = false;
        }
        if (success === false) {
            continue; // retry
        }
        testBalance (exchange, skippedProperties, method, response);
        now = exchange.milliseconds ();
    }
}

export default testWatchBalance;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/pro/test/Exchange/test.watchBalance.ts`.

**Functions defined**: testWatchBalance

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 26
- Comment lines: 1
- Blank lines: 4

### Main Components

**Functions** (1):
- `testWatchBalance()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../test/Exchange/base/test.sharedMethods.js` (imported)
- `../../../test/Exchange/base/test.balance.js` (imported)
- `../../../test/Exchange/base/test.sharedMethods.js` (referenced)
- `../../../test/Exchange/base/test.balance.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/pro/test/Exchange/test.watchBalance.ts
```

