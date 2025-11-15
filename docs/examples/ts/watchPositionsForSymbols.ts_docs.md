# Documentation: examples/ts/watchPositionsForSymbols.ts

## File Metadata

- **Path**: `examples/ts/watchPositionsForSymbols.ts`
- **Size**: 430 bytes
- **Lines**: 17
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import ccxt from '../../js/ccxt.js';

// AUTO-TRANSPILE //

async function example () {
    const exchange = new ccxt.pro.binanceusdm ({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'Your_API_SECRET'
    });
    const symbols = [ 'BTC/USDT:USDT', 'ETH/USDT:USDT', 'DOGE/USDT:USDT' ];
    while (true) {
        const trades = await exchange.watchPositions (symbols);
        console.log (trades);
    }
}
await example ();

```

## High-Level Overview

This is a TypeScript file located at `examples/ts/watchPositionsForSymbols.ts`.

**Functions defined**: example

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 13
- Comment lines: 1
- Blank lines: 3

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

**To execute this TypeScript file:**

```bash
ts-node examples/ts/watchPositionsForSymbols.ts
```

