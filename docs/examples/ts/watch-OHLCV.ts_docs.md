# Documentation: examples/ts/watch-OHLCV.ts

## File Metadata

- **Path**: `examples/ts/watch-OHLCV.ts`
- **Size**: 336 bytes
- **Lines**: 15
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import ccxt from '../../js/ccxt.js';

// AUTO-TRANSPILE //

async function example () {
    const binance = new ccxt.pro.binance ({});
    const symbol = 'BTC/USDT';
    const timeframe = '1m';
    while (true) {
        const ohlcv = await binance.watchOHLCV (symbol, timeframe);
        console.log (ohlcv);
    }
}
await example ();

```

## High-Level Overview

This is a TypeScript file located at `examples/ts/watch-OHLCV.ts`.

**Functions defined**: example

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 15
- Code lines: 11
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
ts-node examples/ts/watch-OHLCV.ts
```

