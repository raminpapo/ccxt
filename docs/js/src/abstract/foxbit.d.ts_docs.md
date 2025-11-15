# Documentation: js/src/abstract/foxbit.d.ts

## File Metadata

- **Path**: `js/src/abstract/foxbit.d.ts`
- **Size**: 1,843 bytes
- **Lines**: 30
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    v3PublicGetCurrencies(params?: {}): Promise<implicitReturnType>;
    v3PublicGetMarkets(params?: {}): Promise<implicitReturnType>;
    v3PublicGetMarketsTicker24hr(params?: {}): Promise<implicitReturnType>;
    v3PublicGetMarketsMarketOrderbook(params?: {}): Promise<implicitReturnType>;
    v3PublicGetMarketsMarketCandlesticks(params?: {}): Promise<implicitReturnType>;
    v3PublicGetMarketsMarketTradesHistory(params?: {}): Promise<implicitReturnType>;
    v3PublicGetMarketsMarketTicker24hr(params?: {}): Promise<implicitReturnType>;
    v3PrivateGetAccounts(params?: {}): Promise<implicitReturnType>;
    v3PrivateGetAccountsSymbolTransactions(params?: {}): Promise<implicitReturnType>;
    v3PrivateGetOrders(params?: {}): Promise<implicitReturnType>;
    v3PrivateGetOrdersByOrderIdId(params?: {}): Promise<implicitReturnType>;
    v3PrivateGetTrades(params?: {}): Promise<implicitReturnType>;
    v3PrivateGetDepositsAddress(params?: {}): Promise<implicitReturnType>;
    v3PrivateGetDeposits(params?: {}): Promise<implicitReturnType>;
    v3PrivateGetWithdrawals(params?: {}): Promise<implicitReturnType>;
    v3PrivateGetMeFeesTrading(params?: {}): Promise<implicitReturnType>;
    v3PrivatePostOrders(params?: {}): Promise<implicitReturnType>;
    v3PrivatePostOrdersBatch(params?: {}): Promise<implicitReturnType>;
    v3PrivatePostOrdersCancelReplace(params?: {}): Promise<implicitReturnType>;
    v3PrivatePostWithdrawals(params?: {}): Promise<implicitReturnType>;
    v3PrivatePutOrdersCancel(params?: {}): Promise<implicitReturnType>;
    statusPublicGetStatus(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/foxbit.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 29
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
ts-node js/src/abstract/foxbit.d.ts
```

