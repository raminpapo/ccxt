# Documentation: js/src/abstract/deepcoin.d.ts

## File Metadata

- **Path**: `js/src/abstract/deepcoin.d.ts`
- **Size**: 4,707 bytes
- **Lines**: 61
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetDeepcoinMarketBooks(params?: {}): Promise<implicitReturnType>;
    publicGetDeepcoinMarketCandles(params?: {}): Promise<implicitReturnType>;
    publicGetDeepcoinMarketInstruments(params?: {}): Promise<implicitReturnType>;
    publicGetDeepcoinMarketTickers(params?: {}): Promise<implicitReturnType>;
    publicGetDeepcoinMarketIndexCandles(params?: {}): Promise<implicitReturnType>;
    publicGetDeepcoinMarketTrades(params?: {}): Promise<implicitReturnType>;
    publicGetDeepcoinMarketMarkPriceCandles(params?: {}): Promise<implicitReturnType>;
    publicGetDeepcoinMarketStepMargin(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinAccountBalances(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinAccountBills(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinAccountPositions(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinTradeFills(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinTradeOrderByID(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinTradeFinishOrderByID(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinTradeOrdersHistory(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinTradeV2OrdersPending(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinTradeFundingRate(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinTradeFundRateCurrentFundingRate(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinTradeFundRateHistory(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinTradeTriggerOrdersPending(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinTradeTriggerOrdersHistory(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinCopytradingSupportContracts(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinCopytradingLeaderPosition(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinCopytradingEstimateProfit(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinCopytradingHistoryProfit(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinCopytradingFollowerRank(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinInternalTransferSupport(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinInternalTransferHistoryOrder(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinRebateConfig(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinAgentsUsers(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinAgentsUsersRebateList(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinAgentsUsersRebates(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinAssetDepositList(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinAssetWithdrawList(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinAssetRechargeChainList(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinListenkeyAcquire(params?: {}): Promise<implicitReturnType>;
    privateGetDeepcoinListenkeyExtend(params?: {}): Promise<implicitReturnType>;
    privatePostDeepcoinAccountSetLeverage(params?: {}): Promise<implicitReturnType>;
    privatePostDeepcoinTradeOrder(params?: {}): Promise<implicitReturnType>;
    privatePostDeepcoinTradeReplaceOrder(params?: {}): Promise<implicitReturnType>;
    privatePostDeepcoinTradeCancelOrder(params?: {}): Promise<implicitReturnType>;
    privatePostDeepcoinTradeBatchCancelOrder(params?: {}): Promise<implicitReturnType>;
    privatePostDeepcoinTradeCancelTriggerOrder(params?: {}): Promise<implicitReturnType>;
    privatePostDeepcoinTradeSwapCancelAll(params?: {}): Promise<implicitReturnType>;
    privatePostDeepcoinTradeTriggerOrder(params?: {}): Promise<implicitReturnType>;
    privatePostDeepcoinTradeBatchClosePosition(params?: {}): Promise<implicitReturnType>;
    privatePostDeepcoinTradeReplaceOrderSltp(params?: {}): Promise<implicitReturnType>;
    privatePostDeepcoinTradeClosePositionByIds(params?: {}): Promise<implicitReturnType>;
    privatePostDeepcoinCopytradingLeaderSettings(params?: {}): Promise<implicitReturnType>;
    privatePostDeepcoinCopytradingSetContracts(params?: {}): Promise<implicitReturnType>;
    privatePostDeepcoinInternalTransfer(params?: {}): Promise<implicitReturnType>;
    privatePostDeepcoinRebateConfig(params?: {}): Promise<implicitReturnType>;
    privatePostDeepcoinAssetTransfer(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/deepcoin.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 61
- Code lines: 60
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
ts-node js/src/abstract/deepcoin.d.ts
```

