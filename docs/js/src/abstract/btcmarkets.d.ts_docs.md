# Documentation: js/src/abstract/btcmarkets.d.ts

## File Metadata

- **Path**: `js/src/abstract/btcmarkets.d.ts`
- **Size**: 2,683 bytes
- **Lines**: 43
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetMarkets(params?: {}): Promise<implicitReturnType>;
    publicGetMarketsMarketIdTicker(params?: {}): Promise<implicitReturnType>;
    publicGetMarketsMarketIdTrades(params?: {}): Promise<implicitReturnType>;
    publicGetMarketsMarketIdOrderbook(params?: {}): Promise<implicitReturnType>;
    publicGetMarketsMarketIdCandles(params?: {}): Promise<implicitReturnType>;
    publicGetMarketsTickers(params?: {}): Promise<implicitReturnType>;
    publicGetMarketsOrderbooks(params?: {}): Promise<implicitReturnType>;
    publicGetTime(params?: {}): Promise<implicitReturnType>;
    privateGetOrders(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersId(params?: {}): Promise<implicitReturnType>;
    privateGetBatchordersIds(params?: {}): Promise<implicitReturnType>;
    privateGetTrades(params?: {}): Promise<implicitReturnType>;
    privateGetTradesId(params?: {}): Promise<implicitReturnType>;
    privateGetWithdrawals(params?: {}): Promise<implicitReturnType>;
    privateGetWithdrawalsId(params?: {}): Promise<implicitReturnType>;
    privateGetDeposits(params?: {}): Promise<implicitReturnType>;
    privateGetDepositsId(params?: {}): Promise<implicitReturnType>;
    privateGetTransfers(params?: {}): Promise<implicitReturnType>;
    privateGetTransfersId(params?: {}): Promise<implicitReturnType>;
    privateGetAddresses(params?: {}): Promise<implicitReturnType>;
    privateGetWithdrawalFees(params?: {}): Promise<implicitReturnType>;
    privateGetAssets(params?: {}): Promise<implicitReturnType>;
    privateGetAccountsMeTradingFees(params?: {}): Promise<implicitReturnType>;
    privateGetAccountsMeWithdrawalLimits(params?: {}): Promise<implicitReturnType>;
    privateGetAccountsMeBalances(params?: {}): Promise<implicitReturnType>;
    privateGetAccountsMeTransactions(params?: {}): Promise<implicitReturnType>;
    privateGetReportsId(params?: {}): Promise<implicitReturnType>;
    privatePostOrders(params?: {}): Promise<implicitReturnType>;
    privatePostBatchorders(params?: {}): Promise<implicitReturnType>;
    privatePostWithdrawals(params?: {}): Promise<implicitReturnType>;
    privatePostReports(params?: {}): Promise<implicitReturnType>;
    privateDeleteOrders(params?: {}): Promise<implicitReturnType>;
    privateDeleteOrdersId(params?: {}): Promise<implicitReturnType>;
    privateDeleteBatchordersIds(params?: {}): Promise<implicitReturnType>;
    privatePutOrdersId(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/btcmarkets.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 43
- Code lines: 42
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
ts-node js/src/abstract/btcmarkets.d.ts
```

