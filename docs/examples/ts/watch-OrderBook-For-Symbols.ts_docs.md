# Documentation: examples/ts/watch-OrderBook-For-Symbols.ts

## File Metadata

- **Path**: `examples/ts/watch-OrderBook-For-Symbols.ts`
- **Size**: 404 bytes
- **Lines**: 14
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import ccxt from '../../js/ccxt.js';

// AUTO-TRANSPILE //

async function example () {
    const binance = new ccxt.pro.binance ({});
    const symbols = [ 'BTC/USDT', 'ETH/USDT', 'DOGE/USDT' ];
    while (true) {
        const orderbook = await binance.watchOrderBookForSymbols (symbols);
        console.log (orderbook['symbol'], orderbook['asks'][0], orderbook['bids'][0]);
    }
}
await example ();

```

## High-Level Overview

This is a TypeScript file located at `examples/ts/watch-OrderBook-For-Symbols.ts`.

**Functions defined**: example

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 14
- Code lines: 10
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
ts-node examples/ts/watch-OrderBook-For-Symbols.ts
```

