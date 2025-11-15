# Documentation: examples/ccxt.pro/js/gateio-watch-balance.js

## File Metadata

- **Path**: `examples/ccxt.pro/js/gateio-watch-balance.js`
- **Size**: 581 bytes
- **Lines**: 24
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
const ccxt = require ('../../../ccxt')

console.log ('CCXT Pro version:', ccxt.version)

async function main () {
     const exchange = new ccxt.pro.gateio ({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
    })
    await exchange.loadMarkets ()
    exchange.verbose = true
    while (true) {
        try {
            const response = await exchange.watchBalance ()
            console.log (new Date (), response)
        } catch (e) {
            console.log (e.constructor.name, e.message)
            await exchange.sleep (1000)
        }
    }
}

main ()

```

## High-Level Overview

This is a JavaScript file located at `examples/ccxt.pro/js/gateio-watch-balance.js`.

**Functions defined**: main



## Detailed Walkthrough

### Code Structure

- Total lines: 24
- Code lines: 20
- Comment lines: 0
- Blank lines: 4

### Main Components

**Functions** (1):
- `main()`



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
node examples/ccxt.pro/js/gateio-watch-balance.js
```

