# Documentation: examples/js/binance-universal-transfer.js

## File Metadata

- **Path**: `examples/js/binance-universal-transfer.js`
- **Size**: 617 bytes
- **Lines**: 17
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import ccxt from '../../js/ccxt.js';

(async () => {

    // apiKey must have universal transfer permissions
    const binance = new ccxt.binance ({
        "apiKey": "",
        "secret": "",
    })

    console.log (await binance.transfer ('USDT', 1, 'spot', 'future'))
    const transfers = await binance.fetchTransfers ();
    console.log ('got ', transfers.length, ' transfers')
    console.log (await binance.transfer ('USDT', 1, 'spot', 'cross')) // For transfer to cross margin wallet
    console.log (await binance.transfer ('USDT', 1, 'spot', 'ADA/USDT')) // For transfer to an isolated margin wallet
}) ()

```

## High-Level Overview

This is a JavaScript file located at `examples/js/binance-universal-transfer.js`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 12
- Comment lines: 1
- Blank lines: 4

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/binance-universal-transfer.js
```

