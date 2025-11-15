# Documentation: js/src/abstract/p2b.d.ts

## File Metadata

- **Path**: `js/src/abstract/p2b.d.ts`
- **Size**: 1,479 bytes
- **Lines**: 26
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetMarkets(params?: {}): Promise<implicitReturnType>;
    publicGetMarket(params?: {}): Promise<implicitReturnType>;
    publicGetTickers(params?: {}): Promise<implicitReturnType>;
    publicGetTicker(params?: {}): Promise<implicitReturnType>;
    publicGetBook(params?: {}): Promise<implicitReturnType>;
    publicGetHistory(params?: {}): Promise<implicitReturnType>;
    publicGetDepthResult(params?: {}): Promise<implicitReturnType>;
    publicGetMarketKline(params?: {}): Promise<implicitReturnType>;
    privatePostAccountBalances(params?: {}): Promise<implicitReturnType>;
    privatePostAccountBalance(params?: {}): Promise<implicitReturnType>;
    privatePostOrderNew(params?: {}): Promise<implicitReturnType>;
    privatePostOrderCancel(params?: {}): Promise<implicitReturnType>;
    privatePostOrders(params?: {}): Promise<implicitReturnType>;
    privatePostAccountMarketOrderHistory(params?: {}): Promise<implicitReturnType>;
    privatePostAccountMarketDealHistory(params?: {}): Promise<implicitReturnType>;
    privatePostAccountOrder(params?: {}): Promise<implicitReturnType>;
    privatePostAccountOrderHistory(params?: {}): Promise<implicitReturnType>;
    privatePostAccountExecutedHistory(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/p2b.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 25
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
ts-node js/src/abstract/p2b.d.ts
```

