# Documentation: examples/ts/fetch-futures/src/index.ts

## File Metadata

- **Path**: `examples/ts/fetch-futures/src/index.ts`
- **Size**: 907 bytes
- **Lines**: 29
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
// Example code in typescript
// Based on /examples/js/fetch-okex-futures.js

import * as ccxt from 'ccxt';
const log = require('ololog');

const fetchFutures = async () => {
    const exchange = new ccxt.bitmex();
    exchange.markets = await exchange.loadMarkets(true);

    for (let symbol in exchange.markets) {
        log('----------------------------------------------------');
        log(`symbol = ${symbol}`);
        try {
            const market = exchange.markets[symbol];
            if (market['future']) {
                const ticker = await exchange.fetchTicker(symbol);
                log('----------------------------------------------------');
                log(symbol, ticker);
                await (ccxt as any).sleep(exchange.rateLimit); // Missing type information.
            }
        } catch (error) {
            log('error =', error);
        }
    }
};

fetchFutures();

```

## High-Level Overview

This is a TypeScript file located at `examples/ts/fetch-futures/src/index.ts`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 22
- Comment lines: 2
- Blank lines: 5

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `ccxt` (imported)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node examples/ts/fetch-futures/src/index.ts
```

