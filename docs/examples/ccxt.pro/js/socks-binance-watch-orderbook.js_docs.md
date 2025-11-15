# Documentation: examples/ccxt.pro/js/socks-binance-watch-orderbook.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/socks-binance-watch-orderbook.js`
- **Size**: 938 bytes
- **Lines**: 30
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('ccxt')
    , SocksProxyAgent = require ('socks-proxy-agent')
    , socks = 'socks://127.0.0.1:7000'
    , socksAgent = new SocksProxyAgent (socks)
    , exchange = new ccxt.binance ({
        enableRatLimit: true,
        httpsAgent: socksAgent, // ←--------------------- socksAgent here
        options: {
            'ws': {
                'options': { agent: socksAgent }, // ←--- socksAgent here
            },
        },
    })

;(async () => {
    console.log (socks)
    const symbol = 'BTC/USDT'
    await exchange.loadMarkets ()
    console.log ('Markets loaded')
    while (true) {
        try {
            const orderbook = await exchange.watchOrderBook (symbol)
            console.log (exchange.iso8601 (exchange.milliseconds()), symbol, orderbook['asks'][0], orderbook['bids'][0])
        } catch (e) {
            console.log (e.constructor.name, e.message)
        }
    }
}) ()
```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/socks-binance-watch-orderbook.js`.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 28
- Comment lines: 0
- Blank lines: 2

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/ccxt.pro/js/socks-binance-watch-orderbook.js
```

