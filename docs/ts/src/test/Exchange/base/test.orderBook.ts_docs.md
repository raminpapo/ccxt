# Documentation: ts/src/test/Exchange/base/test.orderBook.ts

## File Metadata

- **Path**: `ts/src/test/Exchange/base/test.orderBook.ts`
- **Size**: 3,816 bytes
- **Lines**: 75
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import assert from 'assert';
import { Exchange, OrderBook } from "../../../../ccxt";
import Precise from '../../../base/Precise.js';
import testSharedMethods from './test.sharedMethods.js';

function testOrderBook (exchange: Exchange, skippedProperties: object, method: string, orderbook: OrderBook, symbol: string | undefined) {
    const format = {
        'symbol': 'ETH/BTC',
        'asks': [
            [ exchange.parseNumber ('1.24'), exchange.parseNumber ('0.453') ],
            [ exchange.parseNumber ('1.25'), exchange.parseNumber ('0.157') ],
        ],
        'bids': [
            [ exchange.parseNumber ('1.23'), exchange.parseNumber ('0.123') ],
            [ exchange.parseNumber ('1.22'), exchange.parseNumber ('0.543') ],
        ],
        'timestamp': 1504224000000,
        'datetime': '2017-09-01T00:00:00',
        'nonce': 134234234,
        // 'info': {},
    };
    const emptyAllowedFor = [ 'nonce' ];
    // turn into copy: https://discord.com/channels/690203284119617602/921046068555313202/1220626834887282728
    orderbook = exchange.deepExtend ({}, orderbook);
    testSharedMethods.assertStructure (exchange, skippedProperties, method, orderbook, format, emptyAllowedFor);
    testSharedMethods.assertTimestampAndDatetime (exchange, skippedProperties, method, orderbook);
    testSharedMethods.assertSymbol (exchange, skippedProperties, method, orderbook, 'symbol', symbol);
    const logText = testSharedMethods.logTemplate (exchange, method, orderbook);
    // todo: check non-emtpy arrays for bids/asks for toptier exchanges
    const bids = orderbook['bids'];
    const bidsLength = bids.length;
    for (let i = 0; i < bidsLength; i++) {
        const currentBidString = exchange.safeString (bids[i], 0);
        if (!('compareToNextItem' in skippedProperties)) {
            const nextI = i + 1;
            if (bidsLength > nextI) {
                const nextBidString = exchange.safeString (bids[nextI], 0);
                assert (Precise.stringGt (currentBidString, nextBidString), 'current bid should be > than the next one: ' + currentBidString + '>' + nextBidString + logText);
            }
        }
        if (!('compareToZero' in skippedProperties)) {
            // compare price & volume to zero
            testSharedMethods.assertGreater (exchange, skippedProperties, method, bids[i], 0, '0');
            testSharedMethods.assertGreater (exchange, skippedProperties, method, bids[i], 1, '0');
        }
    }
    const asks = orderbook['asks'];
    const asksLength = asks.length;
    for (let i = 0; i < asksLength; i++) {
        const currentAskString = exchange.safeString (asks[i], 0);
        if (!('compareToNextItem' in skippedProperties)) {
            const nextI = i + 1;
            if (asksLength > nextI) {
                const nextAskString = exchange.safeString (asks[nextI], 0);
                assert (Precise.stringLt (currentAskString, nextAskString), 'current ask should be < than the next one: ' + currentAskString + '<' + nextAskString + logText);
            }
        }
        if (!('compareToZero' in skippedProperties)) {
            // compare price & volume to zero
            testSharedMethods.assertGreater (exchange, skippedProperties, method, asks[i], 0, '0');
            testSharedMethods.assertGreater (exchange, skippedProperties, method, asks[i], 1, '0');
        }
    }
    if (!('spread' in skippedProperties)) {
        if (bidsLength && asksLength) {
            const firstBid = exchange.safeString (bids[0], 0);
            const firstAsk = exchange.safeString (asks[0], 0);
            // check bid-ask spread
            assert (Precise.stringLt (firstBid, firstAsk), 'bids[0][0] (' + firstBid + ') should be < than asks[0][0] (' + firstAsk + ')' + logText);
        }
    }
}

export default testOrderBook;

```

## High-Level Overview

This is a TypeScript file located at `ts/src/test/Exchange/base/test.orderBook.ts`.

**Functions defined**: testOrderBook

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 75
- Code lines: 66
- Comment lines: 6
- Blank lines: 3

### Main Components

**Functions** (1):
- `testOrderBook()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./test.sharedMethods.js` (imported)
- `../../../../ccxt` (imported)
- `../../../base/Precise.js` (imported)
- `assert` (imported)
- `./test.sharedMethods.js` (referenced)
- `../../../base/Precise.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/test/Exchange/base/test.orderBook.ts
```

