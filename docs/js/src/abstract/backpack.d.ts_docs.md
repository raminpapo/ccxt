# Documentation: js/src/abstract/backpack.d.ts

## File Metadata

- **Path**: `js/src/abstract/backpack.d.ts`
- **Size**: 4,389 bytes
- **Lines**: 64
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetApiV1Assets(params?: {}): Promise<implicitReturnType>;
    publicGetApiV1Collateral(params?: {}): Promise<implicitReturnType>;
    publicGetApiV1BorrowLendMarkets(params?: {}): Promise<implicitReturnType>;
    publicGetApiV1BorrowLendMarketsHistory(params?: {}): Promise<implicitReturnType>;
    publicGetApiV1Markets(params?: {}): Promise<implicitReturnType>;
    publicGetApiV1Market(params?: {}): Promise<implicitReturnType>;
    publicGetApiV1Ticker(params?: {}): Promise<implicitReturnType>;
    publicGetApiV1Tickers(params?: {}): Promise<implicitReturnType>;
    publicGetApiV1Depth(params?: {}): Promise<implicitReturnType>;
    publicGetApiV1Klines(params?: {}): Promise<implicitReturnType>;
    publicGetApiV1MarkPrices(params?: {}): Promise<implicitReturnType>;
    publicGetApiV1OpenInterest(params?: {}): Promise<implicitReturnType>;
    publicGetApiV1FundingRates(params?: {}): Promise<implicitReturnType>;
    publicGetApiV1Status(params?: {}): Promise<implicitReturnType>;
    publicGetApiV1Ping(params?: {}): Promise<implicitReturnType>;
    publicGetApiV1Time(params?: {}): Promise<implicitReturnType>;
    publicGetApiV1Wallets(params?: {}): Promise<implicitReturnType>;
    publicGetApiV1Trades(params?: {}): Promise<implicitReturnType>;
    publicGetApiV1TradesHistory(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1Account(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1AccountLimitsBorrow(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1AccountLimitsOrder(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1AccountLimitsWithdrawal(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1BorrowLendPositions(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1Capital(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1CapitalCollateral(params?: {}): Promise<implicitReturnType>;
    privateGetWapiV1CapitalDeposits(params?: {}): Promise<implicitReturnType>;
    privateGetWapiV1CapitalDepositAddress(params?: {}): Promise<implicitReturnType>;
    privateGetWapiV1CapitalWithdrawals(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1Position(params?: {}): Promise<implicitReturnType>;
    privateGetWapiV1HistoryBorrowLend(params?: {}): Promise<implicitReturnType>;
    privateGetWapiV1HistoryInterest(params?: {}): Promise<implicitReturnType>;
    privateGetWapiV1HistoryBorrowLendPositions(params?: {}): Promise<implicitReturnType>;
    privateGetWapiV1HistoryDust(params?: {}): Promise<implicitReturnType>;
    privateGetWapiV1HistoryFills(params?: {}): Promise<implicitReturnType>;
    privateGetWapiV1HistoryFunding(params?: {}): Promise<implicitReturnType>;
    privateGetWapiV1HistoryOrders(params?: {}): Promise<implicitReturnType>;
    privateGetWapiV1HistoryRfq(params?: {}): Promise<implicitReturnType>;
    privateGetWapiV1HistoryQuote(params?: {}): Promise<implicitReturnType>;
    privateGetWapiV1HistorySettlement(params?: {}): Promise<implicitReturnType>;
    privateGetWapiV1HistoryStrategies(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1Order(params?: {}): Promise<implicitReturnType>;
    privateGetApiV1Orders(params?: {}): Promise<implicitReturnType>;
    privatePostApiV1AccountConvertDust(params?: {}): Promise<implicitReturnType>;
    privatePostApiV1BorrowLend(params?: {}): Promise<implicitReturnType>;
    privatePostWapiV1CapitalWithdrawals(params?: {}): Promise<implicitReturnType>;
    privatePostApiV1Order(params?: {}): Promise<implicitReturnType>;
    privatePostApiV1Orders(params?: {}): Promise<implicitReturnType>;
    privatePostApiV1Rfq(params?: {}): Promise<implicitReturnType>;
    privatePostApiV1RfqAccept(params?: {}): Promise<implicitReturnType>;
    privatePostApiV1RfqRefresh(params?: {}): Promise<implicitReturnType>;
    privatePostApiV1RfqCancel(params?: {}): Promise<implicitReturnType>;
    privatePostApiV1RfqQuote(params?: {}): Promise<implicitReturnType>;
    privateDeleteApiV1Order(params?: {}): Promise<implicitReturnType>;
    privateDeleteApiV1Orders(params?: {}): Promise<implicitReturnType>;
    privatePatchApiV1Account(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/backpack.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 64
- Code lines: 63
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
ts-node js/src/abstract/backpack.d.ts
```

