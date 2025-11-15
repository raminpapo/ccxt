# Documentation: ts/src/pro/test/base/test.close.ts

## File Metadata

- **Path**: `ts/src/pro/test/base/test.close.ts`
- **Size**: 2,503 bytes
- **Lines**: 81
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { sleep } from '../../../base/functions.js';
import { ExchangeClosedByUser } from '../../../base/errors.js';
import ccxt, { Exchange } from '../../../../ccxt.js';

async function watchTickerLoop (exchange) {
    const method = 'watchTicker';
    /* eslint-disable */
    while (true) {
        console.log ('creating future');
        const ticker = await exchange.watchTicker ('BTC/USDT');
        console.log ('ticker recieved, future resolved');
    }
}

async function watchOrderBookForSymbolsLoop (exchange: Exchange) {
    const method = 'watchTicker';
    /* eslint-disable */
    while (true) {
        const trades = await exchange.watchTradesForSymbols ([ 'BTC/USDT', 'ETH/USDT', 'LTC/USDT' ]);
    }
}

async function closeAfter (exchange, ms) {
    await sleep (ms);
    await exchange.close ();
}

async function testWsClose () {
    const exchange = new ccxt.pro.binance ();

    // --------------------------------------------

    console.log ('Testing exchange.close(): No future awaiting, should close with no errors');
    await exchange.watchTicker ('BTC/USDT');
    console.log ('ticker received');
    await exchange.close ();
    console.log ('PASSED - exchange closed with no errors');

    // --------------------------------------------

    console.log ('Testing exchange.close(): call watch_multiple, resolve, should close with no errors');
    await exchange.watchTradesForSymbols ([ 'BTC/USDT', 'ETH/USDT' ]);
    console.log ('ticker received');
    await exchange.close ();
    console.log ('PASSED - exchange closed with no errors');

    // --------------------------------------------

    
    console.log ('Testing exchange.close(): Awaiting future should throw ClosedByUser');
    try {
        closeAfter (exchange, 5000);
        await watchTickerLoop (exchange);
    } catch (e) {
        if (e instanceof ExchangeClosedByUser) {
            console.log ('PASSED - future rejected with ClosedByUser');
        } else {
            throw e;
        }
    }

    // --------------------------------------------

    console.log ('Test exchange.close(): Call watch_multiple unhandled futures are canceled');
    try {
        closeAfter (exchange, 5000);
        await watchOrderBookForSymbolsLoop (exchange);
    } catch (e) {
        if (e instanceof ExchangeClosedByUser) {
            console.log ('PASSED - future rejected with ClosedByUser');
        } else {
            throw e;
        }
    }

    process.exit (0);
}

export default testWsClose;


```

## High-Level Overview

This is a TypeScript file located at `ts/src/pro/test/base/test.close.ts`.

**Functions defined**: watchOrderBookForSymbolsLoop, testWsClose, closeAfter, watchTickerLoop

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 81
- Code lines: 60
- Comment lines: 6
- Blank lines: 15

### Main Components

**Functions** (4):
- `closeAfter()`
- `testWsClose()`
- `watchOrderBookForSymbolsLoop()`
- `watchTickerLoop()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../../base/errors.js` (imported)
- `../../../../ccxt.js` (imported)
- `../../../base/functions.js` (imported)
- `../../../base/errors.js` (referenced)
- `../../../../ccxt.js` (referenced)
- `../../../base/functions.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test ts/src/pro/test/base/test.close.ts
```

