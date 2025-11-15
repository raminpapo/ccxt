# Documentation: examples/ts/fetch-tickers/src/index.ts

## File Metadata

- **Path**: `examples/ts/fetch-tickers/src/index.ts`
- **Size**: 759 bytes
- **Lines**: 22
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
// Example code in typescript
// Based on /examples/js/fetch-from-many-exchanges-simultaneously.js

import * as ccxt from 'ccxt';
const log = require('ololog');

const symbol = 'BTC/USD';
const exchanges = ['coinbasepro', 'gemini', 'kraken'];

const fetchTickers = async (symbol: string) => {
    const result = await Promise.all(exchanges.map(async (id: string): Promise<ccxt.Exchange> => {
        const CCXT = ccxt as any; // Hack!
        const exchange = new CCXT[id]({ 'enableRateLimit': true }) as ccxt.Exchange;
        const ticker = await exchange.fetchTicker(symbol);
        const exchangeExtended = exchange.extend({ 'exchange': id }, ticker) as ccxt.Exchange;
        return exchangeExtended;
    }));
    log(result);
};

fetchTickers(symbol);

```

## High-Level Overview

This is a TypeScript file located at `examples/ts/fetch-tickers/src/index.ts`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 15
- Comment lines: 2
- Blank lines: 5

### Main Components

**Constants** (1):
- `CCXT`



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
ts-node examples/ts/fetch-tickers/src/index.ts
```

