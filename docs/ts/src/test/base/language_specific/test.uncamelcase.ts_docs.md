# Documentation: ts/src/test/base/language_specific/test.uncamelcase.ts

## File Metadata

- **Path**: `ts/src/test/base/language_specific/test.uncamelcase.ts`
- **Size**: 876 bytes
- **Lines**: 23
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
// @ts-nocheck

import assert, { strictEqual, deepEqual } from 'assert';
import ccxt, { Exchange, functions } from '../../../../ccxt.js';

const { index, aggregate, unCamelCase } = functions;

const equal = strictEqual;

function testUnCamelCase () {
    equal (unCamelCase ('parseOHLCVs'), 'parse_ohlcvs');
    equal (unCamelCase ('safeString2'), 'safe_string_2');
    equal (unCamelCase ('safeStringN'), 'safe_string_n');
    equal (unCamelCase ('convertOHLCVToTradingView'), 'convert_ohlcv_to_trading_view');
    equal (unCamelCase ('fetchL2OrderBook'), 'fetch_l2_order_book');
    equal (unCamelCase ('stringToBase64'), 'string_to_base64');
    equal (unCamelCase ('base64ToString'), 'base64_to_string');
    equal (unCamelCase ('parseHTTPResponse'), 'parse_http_response');
    equal (unCamelCase ('hasFetchOHLCV'), 'has_fetch_ohlcv');
}

export default testUnCamelCase;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/base/language_specific/test.uncamelcase.ts`.

**Functions defined**: testUnCamelCase

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 16
- Comment lines: 1
- Blank lines: 6

### Main Components

**Functions** (1):
- `testUnCamelCase()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../../../../ccxt.js` (imported)
- `assert` (imported)
- `../../../../ccxt.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/base/language_specific/test.uncamelcase.ts
```

