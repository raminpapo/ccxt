# Documentation: js/src/abstract/toobit.d.ts

## File Metadata

- **Path**: `js/src/abstract/toobit.d.ts`
- **Size**: 4,816 bytes
- **Lines**: 67
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    commonGetApiV1Time(params?: {}): Promise<implicitReturnType>;
    commonGetApiV1Ping(params?: {}): Promise<implicitReturnType>;
    commonGetApiV1ExchangeInfo(params?: {}): Promise<implicitReturnType>;
    commonGetQuoteV1Depth(params?: {}): Promise<implicitReturnType>;
    commonGetQuoteV1DepthMerged(params?: {}): Promise<implicitReturnType>;
    commonGetQuoteV1Trades(params?: {}): Promise<implicitReturnType>;
    commonGetQuoteV1Klines(params?: {}): Promise<implicitReturnType>;
    commonGetQuoteV1IndexKlines(params?: {}): Promise<implicitReturnType>;
    commonGetQuoteV1MarkPriceKlines(params?: {}): Promise<implicitReturnType>;
    commonGetQuoteV1MarkPrice(params?: {}): Promise<implicitReturnType>;
    commonGetQuoteV1Index(params?: {}): Promise<implicitReturnType>;
    commonGetQuoteV1Ticker24hr(params?: {}): Promise<implicitReturnType>;
    commonGetQuoteV1ContractTicker24hr(params?: {}): Promise<implicitReturnType>;
    commonGetQuoteV1TickerPrice(params?: {}): Promise<implicitReturnType>;
    commonGetQuoteV1TickerBookTicker(params?: {}): Promise<implicitReturnType>;
    commonGetApiV1FuturesFundingRate(params?: {}): Promise<implicitReturnType>;
    commonGetApiV1FuturesHistoryFundingRate(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1Account(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1AccountCheckApiKey(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1SpotOrder(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1SpotOpenOrders(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1FuturesOpenOrders(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1SpotTradeOrders(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1FuturesHistoryOrders(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1AccountTrades(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1AccountBalanceFlow(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1AccountDepositOrders(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1AccountWithdrawOrders(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1AccountDepositAddress(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1SubAccount(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1FuturesAccountLeverage(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1FuturesOrder(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1FuturesPositions(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1FuturesBalance(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1FuturesUserTrades(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1FuturesBalanceFlow(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1FuturesCommissionRate(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1FuturesTodayPnl(params?: {}): Promise<implicitReturnType>;
    privatePostApiV1SpotOrderTest(params?: {}): Promise<implicitReturnType>;
    privatePostApiV1SpotOrder(params?: {}): Promise<implicitReturnType>;
    privatePostApiV1FuturesOrder(params?: {}): Promise<implicitReturnType>;
    privatePostApiV1SpotBatchOrders(params?: {}): Promise<implicitReturnType>;
    privatePostApiV1SubAccountTransfer(params?: {}): Promise<implicitReturnType>;
    privatePostApiV1AccountWithdraw(params?: {}): Promise<implicitReturnType>;
    privatePostApiV1FuturesMarginType(params?: {}): Promise<implicitReturnType>;
    privatePostApiV1FuturesLeverage(params?: {}): Promise<implicitReturnType>;
    privatePostApiV1FuturesBatchOrders(params?: {}): Promise<implicitReturnType>;
    privatePostApiV1FuturesPositionTradingStop(params?: {}): Promise<implicitReturnType>;
    privatePostApiV1FuturesPositionMargin(params?: {}): Promise<implicitReturnType>;
    privatePostApiV1UserDataStream(params?: {}): Promise<implicitReturnType>;
    privatePostApiV1ListenKey(params?: {}): Promise<implicitReturnType>;
    privateDeleteApiV1SpotOrder(params?: {}): Promise<implicitReturnType>;
    privateDeleteApiV1FuturesOrder(params?: {}): Promise<implicitReturnType>;
    privateDeleteApiV1SpotOpenOrders(params?: {}): Promise<implicitReturnType>;
    privateDeleteApiV1FuturesBatchOrders(params?: {}): Promise<implicitReturnType>;
    privateDeleteApiV1SpotCancelOrderByIds(params?: {}): Promise<implicitReturnType>;
    privateDeleteApiV1FuturesCancelOrderByIds(params?: {}): Promise<implicitReturnType>;
    privateDeleteApiV1ListenKey(params?: {}): Promise<implicitReturnType>;
    privatePutApiV1ListenKey(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/toobit.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 67
- Code lines: 66
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
ts-node js/src/abstract/toobit.d.ts
```

