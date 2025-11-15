# Documentation: examples/ts/how-to-import-one-exchange-esm.ts

## File Metadata

- **Path**: `examples/ts/how-to-import-one-exchange-esm.ts`
- **Size**: 294 bytes
- **Lines**: 12
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { binance } from '../../js/ccxt.js';

async function example () {
    const exchange = new binance ({});
    const ob = await exchange.fetchOrderBook ('BTC/USDT', 3);
    const asks = ob['asks'];
    const bids = ob['bids'];
    console.log (asks);
    console.log (bids);
}
example ();

```

## High-Level Overview

This is a TypeScript file located at `examples/ts/how-to-import-one-exchange-esm.ts`.

**Functions defined**: example

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 12
- Code lines: 10
- Comment lines: 0
- Blank lines: 2

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
ts-node examples/ts/how-to-import-one-exchange-esm.ts
```

