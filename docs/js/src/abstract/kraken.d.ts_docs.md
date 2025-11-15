# Documentation: js/src/abstract/kraken.d.ts

## File Metadata

- **Path**: `js/src/abstract/kraken.d.ts`
- **Size**: 4,014 bytes
- **Lines**: 62
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    zendeskGet360000292886(params?: {}): Promise<implicitReturnType>;
    zendeskGet201893608(params?: {}): Promise<implicitReturnType>;
    publicGetAssets(params?: {}): Promise<implicitReturnType>;
    publicGetAssetPairs(params?: {}): Promise<implicitReturnType>;
    publicGetDepth(params?: {}): Promise<implicitReturnType>;
    publicGetOHLC(params?: {}): Promise<implicitReturnType>;
    publicGetSpread(params?: {}): Promise<implicitReturnType>;
    publicGetSystemStatus(params?: {}): Promise<implicitReturnType>;
    publicGetTicker(params?: {}): Promise<implicitReturnType>;
    publicGetTime(params?: {}): Promise<implicitReturnType>;
    publicGetTrades(params?: {}): Promise<implicitReturnType>;
    privatePostAddOrder(params?: {}): Promise<implicitReturnType>;
    privatePostAddOrderBatch(params?: {}): Promise<implicitReturnType>;
    privatePostAddExport(params?: {}): Promise<implicitReturnType>;
    privatePostAmendOrder(params?: {}): Promise<implicitReturnType>;
    privatePostBalance(params?: {}): Promise<implicitReturnType>;
    privatePostCancelAll(params?: {}): Promise<implicitReturnType>;
    privatePostCancelAllOrdersAfter(params?: {}): Promise<implicitReturnType>;
    privatePostCancelOrder(params?: {}): Promise<implicitReturnType>;
    privatePostCancelOrderBatch(params?: {}): Promise<implicitReturnType>;
    privatePostClosedOrders(params?: {}): Promise<implicitReturnType>;
    privatePostDepositAddresses(params?: {}): Promise<implicitReturnType>;
    privatePostDepositMethods(params?: {}): Promise<implicitReturnType>;
    privatePostDepositStatus(params?: {}): Promise<implicitReturnType>;
    privatePostEditOrder(params?: {}): Promise<implicitReturnType>;
    privatePostExportStatus(params?: {}): Promise<implicitReturnType>;
    privatePostGetWebSocketsToken(params?: {}): Promise<implicitReturnType>;
    privatePostLedgers(params?: {}): Promise<implicitReturnType>;
    privatePostOpenOrders(params?: {}): Promise<implicitReturnType>;
    privatePostOpenPositions(params?: {}): Promise<implicitReturnType>;
    privatePostQueryLedgers(params?: {}): Promise<implicitReturnType>;
    privatePostQueryOrders(params?: {}): Promise<implicitReturnType>;
    privatePostQueryTrades(params?: {}): Promise<implicitReturnType>;
    privatePostRetrieveExport(params?: {}): Promise<implicitReturnType>;
    privatePostRemoveExport(params?: {}): Promise<implicitReturnType>;
    privatePostBalanceEx(params?: {}): Promise<implicitReturnType>;
    privatePostTradeBalance(params?: {}): Promise<implicitReturnType>;
    privatePostTradesHistory(params?: {}): Promise<implicitReturnType>;
    privatePostTradeVolume(params?: {}): Promise<implicitReturnType>;
    privatePostWithdraw(params?: {}): Promise<implicitReturnType>;
    privatePostWithdrawCancel(params?: {}): Promise<implicitReturnType>;
    privatePostWithdrawInfo(params?: {}): Promise<implicitReturnType>;
    privatePostWithdrawMethods(params?: {}): Promise<implicitReturnType>;
    privatePostWithdrawAddresses(params?: {}): Promise<implicitReturnType>;
    privatePostWithdrawStatus(params?: {}): Promise<implicitReturnType>;
    privatePostWalletTransfer(params?: {}): Promise<implicitReturnType>;
    privatePostCreateSubaccount(params?: {}): Promise<implicitReturnType>;
    privatePostAccountTransfer(params?: {}): Promise<implicitReturnType>;
    privatePostEarnAllocate(params?: {}): Promise<implicitReturnType>;
    privatePostEarnDeallocate(params?: {}): Promise<implicitReturnType>;
    privatePostEarnAllocateStatus(params?: {}): Promise<implicitReturnType>;
    privatePostEarnDeallocateStatus(params?: {}): Promise<implicitReturnType>;
    privatePostEarnStrategies(params?: {}): Promise<implicitReturnType>;
    privatePostEarnAllocations(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/kraken.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 62
- Code lines: 61
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
ts-node js/src/abstract/kraken.d.ts
```

