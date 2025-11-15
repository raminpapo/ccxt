# Documentation: js/src/abstract/bitbns.d.ts

## File Metadata

- **Path**: `js/src/abstract/bitbns.d.ts`
- **Size**: 2,845 bytes
- **Lines**: 44
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    wwwGetOrderFetchMarkets(params?: {}): Promise<implicitReturnType>;
    wwwGetOrderFetchTickers(params?: {}): Promise<implicitReturnType>;
    wwwGetOrderFetchOrderbook(params?: {}): Promise<implicitReturnType>;
    wwwGetOrderGetTickerWithVolume(params?: {}): Promise<implicitReturnType>;
    wwwGetExchangeDataOhlc(params?: {}): Promise<implicitReturnType>;
    wwwGetExchangeDataOrderBook(params?: {}): Promise<implicitReturnType>;
    wwwGetExchangeDataTradedetails(params?: {}): Promise<implicitReturnType>;
    v1GetPlatformStatus(params?: {}): Promise<implicitReturnType>;
    v1GetTickers(params?: {}): Promise<implicitReturnType>;
    v1GetOrderbookSellSymbol(params?: {}): Promise<implicitReturnType>;
    v1GetOrderbookBuySymbol(params?: {}): Promise<implicitReturnType>;
    v1PostCurrentCoinBalanceEVERYTHING(params?: {}): Promise<implicitReturnType>;
    v1PostGetApiUsageStatusUSAGE(params?: {}): Promise<implicitReturnType>;
    v1PostGetOrderSocketTokenUSAGE(params?: {}): Promise<implicitReturnType>;
    v1PostCurrentCoinBalanceSymbol(params?: {}): Promise<implicitReturnType>;
    v1PostOrderStatusSymbol(params?: {}): Promise<implicitReturnType>;
    v1PostDepositHistorySymbol(params?: {}): Promise<implicitReturnType>;
    v1PostWithdrawHistorySymbol(params?: {}): Promise<implicitReturnType>;
    v1PostWithdrawHistoryAllSymbol(params?: {}): Promise<implicitReturnType>;
    v1PostDepositHistoryAllSymbol(params?: {}): Promise<implicitReturnType>;
    v1PostListOpenOrdersSymbol(params?: {}): Promise<implicitReturnType>;
    v1PostListOpenStopOrdersSymbol(params?: {}): Promise<implicitReturnType>;
    v1PostGetCoinAddressSymbol(params?: {}): Promise<implicitReturnType>;
    v1PostPlaceSellOrderSymbol(params?: {}): Promise<implicitReturnType>;
    v1PostPlaceBuyOrderSymbol(params?: {}): Promise<implicitReturnType>;
    v1PostBuyStopLossSymbol(params?: {}): Promise<implicitReturnType>;
    v1PostSellStopLossSymbol(params?: {}): Promise<implicitReturnType>;
    v1PostCancelOrderSymbol(params?: {}): Promise<implicitReturnType>;
    v1PostCancelStopLossOrderSymbol(params?: {}): Promise<implicitReturnType>;
    v1PostListExecutedOrdersSymbol(params?: {}): Promise<implicitReturnType>;
    v1PostPlaceMarketOrderSymbol(params?: {}): Promise<implicitReturnType>;
    v1PostPlaceMarketOrderQntySymbol(params?: {}): Promise<implicitReturnType>;
    v2PostOrders(params?: {}): Promise<implicitReturnType>;
    v2PostCancel(params?: {}): Promise<implicitReturnType>;
    v2PostGetordersnew(params?: {}): Promise<implicitReturnType>;
    v2PostMarginOrders(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/bitbns.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 43
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
ts-node js/src/abstract/bitbns.d.ts
```

