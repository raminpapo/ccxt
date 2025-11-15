# Documentation: wiki/examples/js/binance-universal-transfer.md

## File Metadata

- **Path**: `wiki/examples/js/binance-universal-transfer.md`
- **Size**: 687 bytes
- **Lines**: 22
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Binance Universal Transfer](./examples/js/)


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/binance-universal-transfer.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 15
- Comment lines: 1
- Blank lines: 6

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

**To execute this Markdown file:**

