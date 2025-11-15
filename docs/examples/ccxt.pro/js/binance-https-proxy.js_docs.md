# Documentation: examples/ccxt.pro/js/binance-https-proxy.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/binance-https-proxy.js`
- **Size**: 1,471 bytes
- **Lines**: 49
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
'use strict';

const ccxt = require ('../../../ccxt')

console.log ('CCXT Version:', ccxt.version)

let HttpsProxyAgent = undefined

try {
    HttpsProxyAgent = require ('https-proxy-agent')
} catch (e) {
    console.log (e.constructor.name, e.message)
    console.log ("\nCould not load the HTTPS proxy agent")
    console.log ("\nPlease, run this command to make sure it's properly installed:")
    console.log ("\nnpm install https-proxy-agent\n")
    process.exit ()
}

async function main () {

    console.log ('Using proxy server', httpsProxyUrl);

    // adjust for your HTTPS proxy URL
    const httpsProxyUrl = process.env.https_proxy || 'https://username:password@your-proxy.com'
        , httpsAgent = new HttpsProxyAgent (httpsProxyUrl)
        , exchange = new ccxt.binance ({
            httpsAgent: httpsAgent, // ←--------------------- httpsAgent here
            options: {
                'ws': {
                    'options': { agent: httpsAgent }, // ←--- httpsAgent here
                },
            },
        })

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
}

main ()

```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/binance-https-proxy.js`.

**Functions defined**: main



## Detailed Walkthrough

### Code Structure

- Total lines: 49
- Code lines: 38
- Comment lines: 1
- Blank lines: 10

### Main Components

**Functions** (1):
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `https://username:password@your-proxy.com` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/ccxt.pro/js/binance-https-proxy.js
```

