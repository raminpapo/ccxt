# Documentation: wiki/examples/ts/watchPositions.md

## File Metadata

- **Path**: `wiki/examples/ts/watchPositions.md`
- **Size**: 405 bytes
- **Lines**: 21
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Watchpositions](./examples/ts/)


 ```javascript
 import ccxt from '../../js/ccxt.js';

// AUTO-TRANSPILE //

async function example () {
    const exchange = new ccxt.pro.binanceusdm ({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_API_SECRET'
    });
    while (true) {
        const trades = await exchange.watchPositions ();
        console.log (trades);
    }
}
await example ();
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/ts/watchPositions.md`.

**Functions defined**: example

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 21
- Code lines: 15
- Comment lines: 1
- Blank lines: 5

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

**To execute this Markdown file:**

