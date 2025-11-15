# Documentation: wiki/examples/js/poll-ohlcv.md

## File Metadata

- **Path**: `wiki/examples/js/poll-ohlcv.md`
- **Size**: 1,443 bytes
- **Lines**: 48
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Poll Ohlcv](./examples/js/)


 ```javascript
 

import ccxt from '../../js/ccxt.js';

const ohlcvsBySymbol = {}

function handleAllOHLCVs (exchange, ohlcvs, symbol, timeframe) {
    console.log ('----------------------------------------------------------')
    console.log ('Last updated:', exchange.iso8601 (exchange.milliseconds ()))
    const symbols = Object.keys (ohlcvsBySymbol)
    for (let i = 0; i < symbols.length; i++) {
        const symbol = symbols[i]
        const ohlcvs = ohlcvsBySymbol[symbol]
        const lastCandle = exchange.safeValue (ohlcvs, ohlcvs.length - 1)
        const lastTimestamp = lastCandle[0]
        console.log (exchange.iso8601 (lastTimestamp), symbol, timeframe, lastCandle.slice (1))
    }
}

async function pollOHLCV (exchange, symbol, timeframe) {
    while (true) {
        try {
            const response = await exchange.fetchOHLCV (symbol, timeframe)
            ohlcvsBySymbol[symbol] = response
            handleAllOHLCVs(exchange, response, symbol, timeframe)
        } catch (e) {
            console.log (e.constructor.name, e.message)
        }
    }
}

async function main () {

    const exchange = new ccxt.binance()
    const markets = await exchange.loadMarkets ()
    const timeframe = '5m'

    const firstOneHundredSymbols = exchange.symbols.slice (0, 100)

    await Promise.all (firstOneHundredSymbols.map (symbol => pollOHLCV (exchange, symbol, timeframe)))
}

main () 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/poll-ohlcv.md`.

**Functions defined**: pollOHLCV, main, handleAllOHLCVs

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 48
- Code lines: 36
- Comment lines: 0
- Blank lines: 12

### Main Components

**Functions** (3):
- `handleAllOHLCVs()`
- `main()`
- `pollOHLCV()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this Markdown file:**

