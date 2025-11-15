# Documentation: examples/js/basic-chart.js

## File Metadata

- **Path**: `examples/js/basic-chart.js`
- **Size**: 943 bytes
- **Lines**: 29
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript


import ccxt from '../../js/ccxt.js';
import asciichart from 'asciichart';
import asTable from 'as-table';
import ololog from 'ololog'
import ansicolor from 'ansicolor';

const log = ololog.configure ({ locate: false })

ansicolor.nice

//-----------------------------------------------------------------------------

;(async function main () {

    // experimental, not yet implemented for all exchanges
    // your contributions are welcome ;)

    const index = 4 // [ timestamp, open, high, low, close, volume ]
    const ohlcv = await new ccxt.okcoin ().fetchOHLCV ('BTC/USD', '15m')
    const lastPrice = ohlcv[ohlcv.length - 1][index] // closing price
    const series = ohlcv.map (x => x[index])         // closing price
    const bitcoinRate = ('₿ = $' + lastPrice).green
    const chart = asciichart.plot (series, { height: 15, padding: '            ' })
    log.yellow ("\n" + chart, bitcoinRate, "\n")
    process.exit ()

}) ()
```

## High-Level Overview

This is a JavaScript file located at `examples/js/basic-chart.js`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 17
- Comment lines: 3
- Blank lines: 9

### Main Components

**Functions** (1):
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `ansicolor` (imported)
- `ololog` (imported)
- `../../js/ccxt.js` (imported)
- `asciichart` (imported)
- `as-table` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/basic-chart.js
```

