# Documentation: js/src/abstract/dydx.d.ts

## File Metadata

- **Path**: `js/src/abstract/dydx.d.ts`
- **Size**: 4,672 bytes
- **Lines**: 62
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    indexerGetAddressesAddress(params?: {}): Promise<implicitReturnType>;
    indexerGetAddressesAddressParentSubaccountNumberNumber(params?: {}): Promise<implicitReturnType>;
    indexerGetAddressesAddressSubaccountNumberSubaccountNumber(params?: {}): Promise<implicitReturnType>;
    indexerGetAssetPositions(params?: {}): Promise<implicitReturnType>;
    indexerGetAssetPositionsParentSubaccountNumber(params?: {}): Promise<implicitReturnType>;
    indexerGetCandlesPerpetualMarketsMarket(params?: {}): Promise<implicitReturnType>;
    indexerGetComplianceScreenAddress(params?: {}): Promise<implicitReturnType>;
    indexerGetFills(params?: {}): Promise<implicitReturnType>;
    indexerGetFillsParentSubaccountNumber(params?: {}): Promise<implicitReturnType>;
    indexerGetFundingPayments(params?: {}): Promise<implicitReturnType>;
    indexerGetFundingPaymentsParentSubaccount(params?: {}): Promise<implicitReturnType>;
    indexerGetHeight(params?: {}): Promise<implicitReturnType>;
    indexerGetHistoricalPnl(params?: {}): Promise<implicitReturnType>;
    indexerGetHistoricalPnlParentSubaccountNumber(params?: {}): Promise<implicitReturnType>;
    indexerGetHistoricalBlockTradingRewardsAddress(params?: {}): Promise<implicitReturnType>;
    indexerGetHistoricalFundingMarket(params?: {}): Promise<implicitReturnType>;
    indexerGetHistoricalTradingRewardAggregationsAddress(params?: {}): Promise<implicitReturnType>;
    indexerGetOrderbooksPerpetualMarketMarket(params?: {}): Promise<implicitReturnType>;
    indexerGetOrders(params?: {}): Promise<implicitReturnType>;
    indexerGetOrdersParentSubaccountNumber(params?: {}): Promise<implicitReturnType>;
    indexerGetOrdersOrderId(params?: {}): Promise<implicitReturnType>;
    indexerGetPerpetualMarkets(params?: {}): Promise<implicitReturnType>;
    indexerGetPerpetualPositions(params?: {}): Promise<implicitReturnType>;
    indexerGetPerpetualPositionsParentSubaccountNumber(params?: {}): Promise<implicitReturnType>;
    indexerGetScreen(params?: {}): Promise<implicitReturnType>;
    indexerGetSparklines(params?: {}): Promise<implicitReturnType>;
    indexerGetTime(params?: {}): Promise<implicitReturnType>;
    indexerGetTradesPerpetualMarketMarket(params?: {}): Promise<implicitReturnType>;
    indexerGetTransfers(params?: {}): Promise<implicitReturnType>;
    indexerGetTransfersBetween(params?: {}): Promise<implicitReturnType>;
    indexerGetTransfersParentSubaccountNumber(params?: {}): Promise<implicitReturnType>;
    indexerGetVaultV1MegavaultHistoricalPnl(params?: {}): Promise<implicitReturnType>;
    indexerGetVaultV1MegavaultPositions(params?: {}): Promise<implicitReturnType>;
    indexerGetVaultV1VaultsHistoricalPnl(params?: {}): Promise<implicitReturnType>;
    indexerGetPerpetualMarketSparklines(params?: {}): Promise<implicitReturnType>;
    indexerGetPerpetualMarketsTicker(params?: {}): Promise<implicitReturnType>;
    indexerGetPerpetualMarketsTickerOrderbook(params?: {}): Promise<implicitReturnType>;
    indexerGetTradesPerpetualMarketTicker(params?: {}): Promise<implicitReturnType>;
    indexerGetHistoricalFundingTicker(params?: {}): Promise<implicitReturnType>;
    indexerGetCandlesTickerResolution(params?: {}): Promise<implicitReturnType>;
    indexerGetAddressesAddressSubaccounts(params?: {}): Promise<implicitReturnType>;
    indexerGetAddressesAddressSubaccountNumberSubaccountNumberAssetPositions(params?: {}): Promise<implicitReturnType>;
    indexerGetAddressesAddressSubaccountNumberSubaccountNumberPerpetualPositions(params?: {}): Promise<implicitReturnType>;
    indexerGetAddressesAddressSubaccountNumberSubaccountNumberOrders(params?: {}): Promise<implicitReturnType>;
    indexerGetFillsParentSubaccount(params?: {}): Promise<implicitReturnType>;
    indexerGetHistoricalPnlParentSubaccount(params?: {}): Promise<implicitReturnType>;
    nodeRpcGetAbciInfo(params?: {}): Promise<implicitReturnType>;
    nodeRpcGetBlock(params?: {}): Promise<implicitReturnType>;
    nodeRpcGetBroadcastTxAsync(params?: {}): Promise<implicitReturnType>;
    nodeRpcGetBroadcastTxSync(params?: {}): Promise<implicitReturnType>;
    nodeRpcGetTx(params?: {}): Promise<implicitReturnType>;
    nodeRestGetCosmosAuthV1beta1AccountInfoDydxAddress(params?: {}): Promise<implicitReturnType>;
    nodeRestPostCosmosTxV1beta1Encode(params?: {}): Promise<implicitReturnType>;
    nodeRestPostCosmosTxV1beta1Simulate(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/dydx.d.ts`.

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
ts-node js/src/abstract/dydx.d.ts
```

