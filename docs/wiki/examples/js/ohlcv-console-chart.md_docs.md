# Documentation: wiki/examples/js/ohlcv-console-chart.md

## File Metadata

- **Path**: `wiki/examples/js/ohlcv-console-chart.md`
- **Size**: 1,050 bytes
- **Lines**: 34
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Ohlcv Console Chart](./examples/js/)


 ```javascript
 

import ccxt from '../../js/ccxt.js';
import asciichart from 'asciichart';
import asTable from 'as-table';
import ololog from 'ololog'
import ansicolor from 'ansicolor';

const log        = ololog.configure ({ locate: false })

ansicolor.nice

//-----------------------------------------------------------------------------

;(async function main () {

    // experimental, not yet implemented for all exchanges
    // your contributions are welcome ;)

    const indexOfClose = 4 // [ timestamp, open, high, low, close, volume ]
    const ohlcv = await new ccxt.cex ().fetchOHLCV ('BTC/USD', '1m')
    const lastPrice = ohlcv[ohlcv.length - 1][indexOfClose] // closing price
    const plotSeriesData = ohlcv.slice (-80).map (x => x[indexOfClose]) // closing price
    const bitcoinRate = ('₿ = $' + lastPrice).green
    const chart = asciichart.plot (plotSeriesData, { height: 15, padding: '            ' })
    log.yellow ("\n" + chart, bitcoinRate, "\n")
    process.exit ()

}) () 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/ohlcv-console-chart.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 20
- Comment lines: 3
- Blank lines: 11

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

**To execute this Markdown file:**

