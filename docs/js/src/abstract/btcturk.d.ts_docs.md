# Documentation: js/src/abstract/btcturk.d.ts

## File Metadata

- **Path**: `js/src/abstract/btcturk.d.ts`
- **Size**: 1,324 bytes
- **Lines**: 24
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetOrderbook(params?: {}): Promise<implicitReturnType>;
    publicGetTicker(params?: {}): Promise<implicitReturnType>;
    publicGetTrades(params?: {}): Promise<implicitReturnType>;
    publicGetOhlc(params?: {}): Promise<implicitReturnType>;
    publicGetServerExchangeinfo(params?: {}): Promise<implicitReturnType>;
    privateGetUsersBalances(params?: {}): Promise<implicitReturnType>;
    privateGetOpenOrders(params?: {}): Promise<implicitReturnType>;
    privateGetAllOrders(params?: {}): Promise<implicitReturnType>;
    privateGetUsersTransactionsTrade(params?: {}): Promise<implicitReturnType>;
    privatePostUsersTransactionsCrypto(params?: {}): Promise<implicitReturnType>;
    privatePostUsersTransactionsFiat(params?: {}): Promise<implicitReturnType>;
    privatePostOrder(params?: {}): Promise<implicitReturnType>;
    privatePostCancelOrder(params?: {}): Promise<implicitReturnType>;
    privateDeleteOrder(params?: {}): Promise<implicitReturnType>;
    graphGetOhlcs(params?: {}): Promise<implicitReturnType>;
    graphGetKlinesHistory(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/btcturk.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 24
- Code lines: 23
- Comment lines: 0
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../base/Exchange.js` (imported)
- `../base/types.js` (imported)
- `../base/Exchange.js` (referenced)
- `../base/types.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node js/src/abstract/btcturk.d.ts
```

