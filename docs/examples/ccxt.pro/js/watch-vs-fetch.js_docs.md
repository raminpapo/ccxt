# Documentation: examples/ccxt.pro/js/watch-vs-fetch.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/watch-vs-fetch.js`
- **Size**: 802 bytes
- **Lines**: 29
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
// see this issue for details
// https://github.com/ccxt/ccxt/issues/6659

const ccxt = require ('ccxt')

 const exchange = new ccxt.pro.kraken ()

function yellow (s) {
    return '\x1b[33m' + s + '\x1b[0m'
}

async function runWs () {
    while (1) {
        const book = await exchange.watchOrderBook ('ETH/BTC')
        console.log (new Date (), 'WS  ', book['datetime'], book['bids'][0][0], book['asks'][0][0])
    }
}

async function runRest () {
    while (1) {
        const book = await exchange.fetchOrderBook ('ETH/BTC')
        const timestamp = new Date (exchange.last_response_headers['Date']).getTime ()
        const datetime = exchange.iso8601 (timestamp)
        console.log (new Date (), 'REST', yellow (datetime), book['bids'][0][0], book['asks'][0][0])
    }
}

runWs ()
runRest ()
```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/watch-vs-fetch.js`.

**Functions defined**: runWs, yellow, runRest



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 21
- Comment lines: 2
- Blank lines: 6

### Main Components

**Functions** (3):
- `runRest()`
- `runWs()`
- `yellow()`



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
node examples/ccxt.pro/js/watch-vs-fetch.js
```

