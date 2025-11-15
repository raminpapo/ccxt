# Documentation: ts/src/test/Exchange/base/test.depositWithdrawal.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/base/test.depositWithdrawal.ts`
- **Size**: 2,114 bytes
- **Lines**: 42
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { Exchange } from "../../../../ccxt";
import testSharedMethods from './test.sharedMethods.js';

function testDepositWithdrawal (exchange: Exchange, skippedProperties: object, method: string, entry: object, requestedCode: string, now: number) {
    const format = {
        'info': {}, // or []
        'id': '1234',
        'txid': '0x1345FEG45EAEF7',
        'timestamp': 1502962946216,
        'datetime': '2017-08-17 12:42:48.000',
        'network': 'ETH',
        'address': '0xEFE3487358AEF352345345',
        'addressTo': '0xEFE3487358AEF352345123',
        'addressFrom': '0xEFE3487358AEF352345456',
        'tag': 'smth',
        'tagTo': 'smth',
        'tagFrom': 'smth',
        'type': 'deposit',
        'amount': exchange.parseNumber ('1.234'),
        'currency': 'USDT',
        'status': 'ok',
        'updated': 1502962946233,
        'fee': {},
    };
    const emptyAllowedFor = [ 'address', 'addressTo', 'addressFrom', 'tag', 'tagTo', 'tagFrom' ]; // below we still do assertion for to/from
    testSharedMethods.assertStructure (exchange, skippedProperties, method, entry, format, emptyAllowedFor);
    testSharedMethods.assertTimestampAndDatetime (exchange, skippedProperties, method, entry, now);
    testSharedMethods.assertCurrencyCode (exchange, skippedProperties, method, entry, entry['currency'], requestedCode);
    //
    testSharedMethods.assertInArray (exchange, skippedProperties, method, entry, 'status', [ 'ok', 'pending', 'failed', 'rejected', 'canceled' ]);
    testSharedMethods.assertInArray (exchange, skippedProperties, method, entry, 'type', [ 'deposit', 'withdrawal' ]);
    testSharedMethods.assertGreaterOrEqual (exchange, skippedProperties, method, entry, 'amount', '0');
    testSharedMethods.assertFeeStructure (exchange, skippedProperties, method, entry, 'fee');
    if (entry['type'] === 'deposit') {
        testSharedMethods.assertType (exchange, skippedProperties, entry, 'addressFrom', format);
    } else {
        testSharedMethods.assertType (exchange, skippedProperties, entry, 'addressTo', format);
    }
}

export default testDepositWithdrawal;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/base/test.depositWithdrawal.ts`.

**Functions defined**: testDepositWithdrawal

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 42
- Code lines: 38
- Comment lines: 1
- Blank lines: 3

### Main Components

**Functions** (1):
- `testDepositWithdrawal()`



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
npm test ts/src/test/Exchange/base/test.depositWithdrawal.ts
```

