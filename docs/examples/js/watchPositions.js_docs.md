# Documentation: examples/js/watchPositions.js

## File Metadata

- **Path**: `examples/js/watchPositions.js`
- **Size**: 340 bytes
- **Lines**: 14
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import ccxt from '../../js/ccxt.js';
// AUTO-TRANSPILE //
async function example() {
    const exchange = new ccxt.pro.binanceusdm({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_API_SECRET'
    });
    while (true) {
        const trades = await exchange.watchPositions();
        console.log(trades);
    }
}
await example();

```

## High-Level Overview

This is a JavaScript file located at `examples/js/watchPositions.js`.

**Functions defined**: example

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 14
- Code lines: 12
- Comment lines: 1
- Blank lines: 1

### Main Components

**Functions** (1):
- `example()`



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
node examples/js/watchPositions.js
```

