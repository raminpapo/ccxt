# Documentation: js/src/abstract/latoken.d.ts

## File Metadata

- **Path**: `js/src/abstract/latoken.d.ts`
- **Size**: 4,243 bytes
- **Lines**: 60
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetBookCurrencyQuote(params?: {}): Promise<implicitReturnType>;
    publicGetChartWeek(params?: {}): Promise<implicitReturnType>;
    publicGetChartWeekCurrencyQuote(params?: {}): Promise<implicitReturnType>;
    publicGetCurrency(params?: {}): Promise<implicitReturnType>;
    publicGetCurrencyAvailable(params?: {}): Promise<implicitReturnType>;
    publicGetCurrencyQuotes(params?: {}): Promise<implicitReturnType>;
    publicGetCurrencyCurrency(params?: {}): Promise<implicitReturnType>;
    publicGetPair(params?: {}): Promise<implicitReturnType>;
    publicGetPairAvailable(params?: {}): Promise<implicitReturnType>;
    publicGetTicker(params?: {}): Promise<implicitReturnType>;
    publicGetTickerBaseQuote(params?: {}): Promise<implicitReturnType>;
    publicGetTime(params?: {}): Promise<implicitReturnType>;
    publicGetTradeHistoryCurrencyQuote(params?: {}): Promise<implicitReturnType>;
    publicGetTradeFeeCurrencyQuote(params?: {}): Promise<implicitReturnType>;
    publicGetTradeFeeLevels(params?: {}): Promise<implicitReturnType>;
    publicGetTransactionBindings(params?: {}): Promise<implicitReturnType>;
    privateGetAuthAccount(params?: {}): Promise<implicitReturnType>;
    privateGetAuthAccountCurrencyCurrencyType(params?: {}): Promise<implicitReturnType>;
    privateGetAuthOrder(params?: {}): Promise<implicitReturnType>;
    privateGetAuthOrderGetOrderId(params?: {}): Promise<implicitReturnType>;
    privateGetAuthOrderPairCurrencyQuote(params?: {}): Promise<implicitReturnType>;
    privateGetAuthOrderPairCurrencyQuoteActive(params?: {}): Promise<implicitReturnType>;
    privateGetAuthStopOrder(params?: {}): Promise<implicitReturnType>;
    privateGetAuthStopOrderGetOrderId(params?: {}): Promise<implicitReturnType>;
    privateGetAuthStopOrderPairCurrencyQuote(params?: {}): Promise<implicitReturnType>;
    privateGetAuthStopOrderPairCurrencyQuoteActive(params?: {}): Promise<implicitReturnType>;
    privateGetAuthTrade(params?: {}): Promise<implicitReturnType>;
    privateGetAuthTradePairCurrencyQuote(params?: {}): Promise<implicitReturnType>;
    privateGetAuthTradeFeeCurrencyQuote(params?: {}): Promise<implicitReturnType>;
    privateGetAuthTransaction(params?: {}): Promise<implicitReturnType>;
    privateGetAuthTransactionBindings(params?: {}): Promise<implicitReturnType>;
    privateGetAuthTransactionBindingsCurrency(params?: {}): Promise<implicitReturnType>;
    privateGetAuthTransactionId(params?: {}): Promise<implicitReturnType>;
    privateGetAuthTransfer(params?: {}): Promise<implicitReturnType>;
    privatePostAuthOrderCancel(params?: {}): Promise<implicitReturnType>;
    privatePostAuthOrderCancelAll(params?: {}): Promise<implicitReturnType>;
    privatePostAuthOrderCancelAllCurrencyQuote(params?: {}): Promise<implicitReturnType>;
    privatePostAuthOrderPlace(params?: {}): Promise<implicitReturnType>;
    privatePostAuthSpotDeposit(params?: {}): Promise<implicitReturnType>;
    privatePostAuthSpotWithdraw(params?: {}): Promise<implicitReturnType>;
    privatePostAuthStopOrderCancel(params?: {}): Promise<implicitReturnType>;
    privatePostAuthStopOrderCancelAll(params?: {}): Promise<implicitReturnType>;
    privatePostAuthStopOrderCancelAllCurrencyQuote(params?: {}): Promise<implicitReturnType>;
    privatePostAuthStopOrderPlace(params?: {}): Promise<implicitReturnType>;
    privatePostAuthTransactionDepositAddress(params?: {}): Promise<implicitReturnType>;
    privatePostAuthTransactionWithdraw(params?: {}): Promise<implicitReturnType>;
    privatePostAuthTransactionWithdrawCancel(params?: {}): Promise<implicitReturnType>;
    privatePostAuthTransactionWithdrawConfirm(params?: {}): Promise<implicitReturnType>;
    privatePostAuthTransactionWithdrawResendCode(params?: {}): Promise<implicitReturnType>;
    privatePostAuthTransferEmail(params?: {}): Promise<implicitReturnType>;
    privatePostAuthTransferId(params?: {}): Promise<implicitReturnType>;
    privatePostAuthTransferPhone(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/latoken.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 60
- Code lines: 59
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
ts-node js/src/abstract/latoken.d.ts
```

