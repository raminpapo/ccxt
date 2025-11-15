# Documentation: utils/test-commonjs.cjs

## File Metadata

- **Path**: `utils/test-commonjs.cjs`
- **Size**: 2,237 bytes
- **Lines**: 63
- **Type**: Unknown
- **Extension**: .cjs


## Original Source Code

```
const ccxt = require ('../dist/ccxt.cjs');
const log = require ('ololog');
const ansi = require ('ansicolor').nice;
const assert = require ('assert');
const fs = require ('fs');
// ----------------------------------------------------------------------------
process.on ('uncaughtException', (e) => {
    console.log (e, e.stack); process.exit (1);
});
process.on ('unhandledRejection', (e) => {
    console.log (e, e.stack); process.exit (1);
});

// ----------------------------------------------------------------------------
// Simple test just to make sure that the CJS code works and it's updated

const CJS_ENTRY_FILE = './dist/cjs/ccxt.js';
const EXCHANGE_FILE = './dist/cjs/src/binance.js'
// const CJS_BUNDLE_FILE = './dist/ccxt.bundle.cjs';
const BROWSER_BUNDLE_FILE = './dist/ccxt.browser.js';

const symbol = 'BTC/USDT:USDT';

function assertGeneratedFilesAreRecent() {
    const now = new Date().getTime();
    const filesToCheck = [CJS_ENTRY_FILE, BROWSER_BUNDLE_FILE, EXCHANGE_FILE];
    for (const file of filesToCheck) {
        var stats = fs.statSync(file);
        var mtime = stats.mtimeMs;
        const diffInSeconds = (now - mtime) / 1000;
        const diffInHours = diffInSeconds / 3600;
        if (diffInHours > 12) {
            log.bright.red('[CJS][Browser][OUT-OF-SYNC] File is outdaded: ' + file);
            process.exit (1);
        }
    }
    log.bright.green('[CJS][Browser] Files are updated');
}

async function main() {
    try {
        assertGeneratedFilesAreRecent();
        // proxy
        // test cjs version
        const exchange = new ccxt.gate({});
        const ticker = await exchange.fetchTicker(symbol);
        assert(ticker !== undefined);
        assert(ticker['symbol'] === symbol);
        log.bright.green('[CJS Code] OK');
        // test cjs bundle version
        // const exchangeBundle = new ccxtBundle.gate({});
        // const tickeBundle = await exchangeBundle.fetchTicker(symbol);
        // assert(tickeBundle !== undefined);
        // assert(tickeBundle['symbol'] === symbol);
        log.bright.green('[CJS Bundle Code] OK');
        process.exit(0);
    } catch (e) {
        log.bright.red('[CJS Code] Error: ' + e);
        process.exit (1);
    }
}

main()
```

## High-Level Overview

This is a Unknown file located at `utils/test-commonjs.cjs`.

**Functions defined**: assertGeneratedFilesAreRecent, main



## Detailed Walkthrough

### Code Structure

- Total lines: 63
- Code lines: 46
- Comment lines: 11
- Blank lines: 6

### Main Components

**Functions** (2):
- `assertGeneratedFilesAreRecent()`
- `main()`

**Constants** (4):
- `BROWSER_BUNDLE_FILE`
- `CJS_BUNDLE_FILE`
- `CJS_ENTRY_FILE`
- `EXCHANGE_FILE`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./dist/cjs/ccxt.js` (referenced)
- `./dist/cjs/src/binance.js` (referenced)
- `./dist/ccxt.bundle.cjs` (referenced)
- `../dist/ccxt.cjs` (referenced)
- `./dist/ccxt.browser.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
