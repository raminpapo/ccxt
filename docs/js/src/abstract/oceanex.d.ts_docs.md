# Documentation: js/src/abstract/oceanex.d.ts

## File Metadata

- **Path**: `js/src/abstract/oceanex.d.ts`
- **Size**: 1,797 bytes
- **Lines**: 31
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetMarkets(params?: {}): Promise<implicitReturnType>;
    publicGetTickersPair(params?: {}): Promise<implicitReturnType>;
    publicGetTickersMulti(params?: {}): Promise<implicitReturnType>;
    publicGetOrderBook(params?: {}): Promise<implicitReturnType>;
    publicGetOrderBookMulti(params?: {}): Promise<implicitReturnType>;
    publicGetFeesTrading(params?: {}): Promise<implicitReturnType>;
    publicGetTrades(params?: {}): Promise<implicitReturnType>;
    publicGetTimestamp(params?: {}): Promise<implicitReturnType>;
    publicPostK(params?: {}): Promise<implicitReturnType>;
    privateGetKey(params?: {}): Promise<implicitReturnType>;
    privateGetMembersMe(params?: {}): Promise<implicitReturnType>;
    privateGetOrders(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersFilter(params?: {}): Promise<implicitReturnType>;
    privatePostOrders(params?: {}): Promise<implicitReturnType>;
    privatePostOrdersMulti(params?: {}): Promise<implicitReturnType>;
    privatePostOrderDelete(params?: {}): Promise<implicitReturnType>;
    privatePostOrderDeleteMulti(params?: {}): Promise<implicitReturnType>;
    privatePostOrdersClear(params?: {}): Promise<implicitReturnType>;
    privatePostWithdrawsSpecialNew(params?: {}): Promise<implicitReturnType>;
    privatePostDepositAddress(params?: {}): Promise<implicitReturnType>;
    privatePostDepositAddresses(params?: {}): Promise<implicitReturnType>;
    privatePostDepositHistory(params?: {}): Promise<implicitReturnType>;
    privatePostWithdrawHistory(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/oceanex.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 30
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
ts-node js/src/abstract/oceanex.d.ts
```

