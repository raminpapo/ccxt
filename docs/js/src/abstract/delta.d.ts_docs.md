# Documentation: js/src/abstract/delta.d.ts

## File Metadata

- **Path**: `js/src/abstract/delta.d.ts`
- **Size**: 3,842 bytes
- **Lines**: 58
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetAssets(params?: {}): Promise<implicitReturnType>;
    publicGetIndices(params?: {}): Promise<implicitReturnType>;
    publicGetProducts(params?: {}): Promise<implicitReturnType>;
    publicGetProductsSymbol(params?: {}): Promise<implicitReturnType>;
    publicGetTickers(params?: {}): Promise<implicitReturnType>;
    publicGetTickersSymbol(params?: {}): Promise<implicitReturnType>;
    publicGetL2orderbookSymbol(params?: {}): Promise<implicitReturnType>;
    publicGetTradesSymbol(params?: {}): Promise<implicitReturnType>;
    publicGetStats(params?: {}): Promise<implicitReturnType>;
    publicGetHistoryCandles(params?: {}): Promise<implicitReturnType>;
    publicGetHistorySparklines(params?: {}): Promise<implicitReturnType>;
    publicGetSettings(params?: {}): Promise<implicitReturnType>;
    privateGetOrders(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersOrderId(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersClientOrderIdClientOid(params?: {}): Promise<implicitReturnType>;
    privateGetProductsProductIdOrdersLeverage(params?: {}): Promise<implicitReturnType>;
    privateGetPositionsMargined(params?: {}): Promise<implicitReturnType>;
    privateGetPositions(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersHistory(params?: {}): Promise<implicitReturnType>;
    privateGetFills(params?: {}): Promise<implicitReturnType>;
    privateGetFillsHistoryDownloadCsv(params?: {}): Promise<implicitReturnType>;
    privateGetWalletBalances(params?: {}): Promise<implicitReturnType>;
    privateGetWalletTransactions(params?: {}): Promise<implicitReturnType>;
    privateGetWalletTransactionsDownload(params?: {}): Promise<implicitReturnType>;
    privateGetWalletsSubAccountsTransferHistory(params?: {}): Promise<implicitReturnType>;
    privateGetUsersTradingPreferences(params?: {}): Promise<implicitReturnType>;
    privateGetSubAccounts(params?: {}): Promise<implicitReturnType>;
    privateGetProfile(params?: {}): Promise<implicitReturnType>;
    privateGetHeartbeat(params?: {}): Promise<implicitReturnType>;
    privateGetDepositsAddress(params?: {}): Promise<implicitReturnType>;
    privatePostOrders(params?: {}): Promise<implicitReturnType>;
    privatePostOrdersBracket(params?: {}): Promise<implicitReturnType>;
    privatePostOrdersBatch(params?: {}): Promise<implicitReturnType>;
    privatePostProductsProductIdOrdersLeverage(params?: {}): Promise<implicitReturnType>;
    privatePostPositionsChangeMargin(params?: {}): Promise<implicitReturnType>;
    privatePostPositionsCloseAll(params?: {}): Promise<implicitReturnType>;
    privatePostWalletsSubAccountBalanceTransfer(params?: {}): Promise<implicitReturnType>;
    privatePostHeartbeatCreate(params?: {}): Promise<implicitReturnType>;
    privatePostHeartbeat(params?: {}): Promise<implicitReturnType>;
    privatePostOrdersCancelAfter(params?: {}): Promise<implicitReturnType>;
    privatePostOrdersLeverage(params?: {}): Promise<implicitReturnType>;
    privatePutOrders(params?: {}): Promise<implicitReturnType>;
    privatePutOrdersBracket(params?: {}): Promise<implicitReturnType>;
    privatePutOrdersBatch(params?: {}): Promise<implicitReturnType>;
    privatePutPositionsAutoTopup(params?: {}): Promise<implicitReturnType>;
    privatePutUsersUpdateMmp(params?: {}): Promise<implicitReturnType>;
    privatePutUsersResetMmp(params?: {}): Promise<implicitReturnType>;
    privateDeleteOrders(params?: {}): Promise<implicitReturnType>;
    privateDeleteOrdersAll(params?: {}): Promise<implicitReturnType>;
    privateDeleteOrdersBatch(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/delta.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 58
- Code lines: 57
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
ts-node js/src/abstract/delta.d.ts
```

