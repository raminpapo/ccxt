# Documentation: js/src/abstract/blofin.d.ts

## File Metadata

- **Path**: `js/src/abstract/blofin.d.ts`
- **Size**: 5,297 bytes
- **Lines**: 71
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetMarketInstruments(params?: {}): Promise<implicitReturnType>;
    publicGetMarketTickers(params?: {}): Promise<implicitReturnType>;
    publicGetMarketBooks(params?: {}): Promise<implicitReturnType>;
    publicGetMarketTrades(params?: {}): Promise<implicitReturnType>;
    publicGetMarketCandles(params?: {}): Promise<implicitReturnType>;
    publicGetMarketMarkPrice(params?: {}): Promise<implicitReturnType>;
    publicGetMarketFundingRate(params?: {}): Promise<implicitReturnType>;
    publicGetMarketFundingRateHistory(params?: {}): Promise<implicitReturnType>;
    privateGetAssetBalances(params?: {}): Promise<implicitReturnType>;
    privateGetTradeOrdersPending(params?: {}): Promise<implicitReturnType>;
    privateGetTradeFillsHistory(params?: {}): Promise<implicitReturnType>;
    privateGetAssetDepositHistory(params?: {}): Promise<implicitReturnType>;
    privateGetAssetWithdrawalHistory(params?: {}): Promise<implicitReturnType>;
    privateGetAssetBills(params?: {}): Promise<implicitReturnType>;
    privateGetAccountBalance(params?: {}): Promise<implicitReturnType>;
    privateGetAccountPositions(params?: {}): Promise<implicitReturnType>;
    privateGetAccountLeverageInfo(params?: {}): Promise<implicitReturnType>;
    privateGetAccountMarginMode(params?: {}): Promise<implicitReturnType>;
    privateGetAccountPositionMode(params?: {}): Promise<implicitReturnType>;
    privateGetAccountBatchLeverageInfo(params?: {}): Promise<implicitReturnType>;
    privateGetTradeOrdersTpslPending(params?: {}): Promise<implicitReturnType>;
    privateGetTradeOrdersAlgoPending(params?: {}): Promise<implicitReturnType>;
    privateGetTradeOrdersHistory(params?: {}): Promise<implicitReturnType>;
    privateGetTradeOrdersTpslHistory(params?: {}): Promise<implicitReturnType>;
    privateGetTradeOrdersAlgoHistory(params?: {}): Promise<implicitReturnType>;
    privateGetTradeOrderPriceRange(params?: {}): Promise<implicitReturnType>;
    privateGetUserQueryApikey(params?: {}): Promise<implicitReturnType>;
    privateGetAffiliateBasic(params?: {}): Promise<implicitReturnType>;
    privateGetCopytradingInstruments(params?: {}): Promise<implicitReturnType>;
    privateGetCopytradingAccountBalance(params?: {}): Promise<implicitReturnType>;
    privateGetCopytradingAccountPositionsByOrder(params?: {}): Promise<implicitReturnType>;
    privateGetCopytradingAccountPositionsDetailsByOrder(params?: {}): Promise<implicitReturnType>;
    privateGetCopytradingAccountPositionsByContract(params?: {}): Promise<implicitReturnType>;
    privateGetCopytradingAccountPositionMode(params?: {}): Promise<implicitReturnType>;
    privateGetCopytradingAccountLeverageInfo(params?: {}): Promise<implicitReturnType>;
    privateGetCopytradingTradeOrdersPending(params?: {}): Promise<implicitReturnType>;
    privateGetCopytradingTradePendingTpslByContract(params?: {}): Promise<implicitReturnType>;
    privateGetCopytradingTradePositionHistoryByOrder(params?: {}): Promise<implicitReturnType>;
    privateGetCopytradingTradeOrdersHistory(params?: {}): Promise<implicitReturnType>;
    privateGetCopytradingTradePendingTpslByOrder(params?: {}): Promise<implicitReturnType>;
    privatePostAccountSetMarginMode(params?: {}): Promise<implicitReturnType>;
    privatePostAccountSetPositionMode(params?: {}): Promise<implicitReturnType>;
    privatePostTradeOrder(params?: {}): Promise<implicitReturnType>;
    privatePostTradeOrderAlgo(params?: {}): Promise<implicitReturnType>;
    privatePostTradeCancelOrder(params?: {}): Promise<implicitReturnType>;
    privatePostTradeCancelAlgo(params?: {}): Promise<implicitReturnType>;
    privatePostAccountSetLeverage(params?: {}): Promise<implicitReturnType>;
    privatePostTradeBatchOrders(params?: {}): Promise<implicitReturnType>;
    privatePostTradeOrderTpsl(params?: {}): Promise<implicitReturnType>;
    privatePostTradeCancelBatchOrders(params?: {}): Promise<implicitReturnType>;
    privatePostTradeCancelTpsl(params?: {}): Promise<implicitReturnType>;
    privatePostTradeClosePosition(params?: {}): Promise<implicitReturnType>;
    privatePostAssetTransfer(params?: {}): Promise<implicitReturnType>;
    privatePostCopytradingAccountSetPositionMode(params?: {}): Promise<implicitReturnType>;
    privatePostCopytradingAccountSetLeverage(params?: {}): Promise<implicitReturnType>;
    privatePostCopytradingTradePlaceOrder(params?: {}): Promise<implicitReturnType>;
    privatePostCopytradingTradeCancelOrder(params?: {}): Promise<implicitReturnType>;
    privatePostCopytradingTradePlaceTpslByContract(params?: {}): Promise<implicitReturnType>;
    privatePostCopytradingTradeCancelTpslByContract(params?: {}): Promise<implicitReturnType>;
    privatePostCopytradingTradePlaceTpslByOrder(params?: {}): Promise<implicitReturnType>;
    privatePostCopytradingTradeCancelTpslByOrder(params?: {}): Promise<implicitReturnType>;
    privatePostCopytradingTradeClosePositionByOrder(params?: {}): Promise<implicitReturnType>;
    privatePostCopytradingTradeClosePositionByContract(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/blofin.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 71
- Code lines: 70
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
ts-node js/src/abstract/blofin.d.ts
```

