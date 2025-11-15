# Documentation: js/src/abstract/coinsph.d.ts

## File Metadata

- **Path**: `js/src/abstract/coinsph.d.ts`
- **Size**: 4,377 bytes
- **Lines**: 58
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetOpenapiV1Ping(params?: {}): Promise<implicitReturnType>;
    publicGetOpenapiV1Time(params?: {}): Promise<implicitReturnType>;
    publicGetOpenapiQuoteV1Ticker24hr(params?: {}): Promise<implicitReturnType>;
    publicGetOpenapiQuoteV1TickerPrice(params?: {}): Promise<implicitReturnType>;
    publicGetOpenapiQuoteV1TickerBookTicker(params?: {}): Promise<implicitReturnType>;
    publicGetOpenapiV1ExchangeInfo(params?: {}): Promise<implicitReturnType>;
    publicGetOpenapiQuoteV1Depth(params?: {}): Promise<implicitReturnType>;
    publicGetOpenapiQuoteV1Klines(params?: {}): Promise<implicitReturnType>;
    publicGetOpenapiQuoteV1Trades(params?: {}): Promise<implicitReturnType>;
    publicGetOpenapiV1Pairs(params?: {}): Promise<implicitReturnType>;
    publicGetOpenapiQuoteV1AvgPrice(params?: {}): Promise<implicitReturnType>;
    privateGetOpenapiWalletV1ConfigGetall(params?: {}): Promise<implicitReturnType>;
    privateGetOpenapiWalletV1DepositAddress(params?: {}): Promise<implicitReturnType>;
    privateGetOpenapiWalletV1DepositHistory(params?: {}): Promise<implicitReturnType>;
    privateGetOpenapiWalletV1WithdrawHistory(params?: {}): Promise<implicitReturnType>;
    privateGetOpenapiV1Account(params?: {}): Promise<implicitReturnType>;
    privateGetOpenapiV1OpenOrders(params?: {}): Promise<implicitReturnType>;
    privateGetOpenapiV1AssetTradeFee(params?: {}): Promise<implicitReturnType>;
    privateGetOpenapiV1Order(params?: {}): Promise<implicitReturnType>;
    privateGetOpenapiV1HistoryOrders(params?: {}): Promise<implicitReturnType>;
    privateGetOpenapiV1MyTrades(params?: {}): Promise<implicitReturnType>;
    privateGetOpenapiV1CapitalDepositHistory(params?: {}): Promise<implicitReturnType>;
    privateGetOpenapiV1CapitalWithdrawHistory(params?: {}): Promise<implicitReturnType>;
    privateGetOpenapiV3PaymentRequestGetPaymentRequest(params?: {}): Promise<implicitReturnType>;
    privateGetMerchantApiV1GetInvoices(params?: {}): Promise<implicitReturnType>;
    privateGetOpenapiAccountV3CryptoAccounts(params?: {}): Promise<implicitReturnType>;
    privateGetOpenapiTransferV3TransfersId(params?: {}): Promise<implicitReturnType>;
    privatePostOpenapiWalletV1WithdrawApply(params?: {}): Promise<implicitReturnType>;
    privatePostOpenapiV1OrderTest(params?: {}): Promise<implicitReturnType>;
    privatePostOpenapiV1Order(params?: {}): Promise<implicitReturnType>;
    privatePostOpenapiV1CapitalWithdrawApply(params?: {}): Promise<implicitReturnType>;
    privatePostOpenapiV1CapitalDepositApply(params?: {}): Promise<implicitReturnType>;
    privatePostOpenapiV3PaymentRequestPaymentRequests(params?: {}): Promise<implicitReturnType>;
    privatePostOpenapiV3PaymentRequestDeletePaymentRequest(params?: {}): Promise<implicitReturnType>;
    privatePostOpenapiV3PaymentRequestPaymentRequestReminder(params?: {}): Promise<implicitReturnType>;
    privatePostOpenapiV1UserDataStream(params?: {}): Promise<implicitReturnType>;
    privatePostMerchantApiV1Invoices(params?: {}): Promise<implicitReturnType>;
    privatePostMerchantApiV1InvoicesCancel(params?: {}): Promise<implicitReturnType>;
    privatePostOpenapiConvertV1GetSupportedTradingPairs(params?: {}): Promise<implicitReturnType>;
    privatePostOpenapiConvertV1GetQuote(params?: {}): Promise<implicitReturnType>;
    privatePostOpenapiConvertV1AccpetQuote(params?: {}): Promise<implicitReturnType>;
    privatePostOpenapiFiatV1SupportChannel(params?: {}): Promise<implicitReturnType>;
    privatePostOpenapiFiatV1CashOut(params?: {}): Promise<implicitReturnType>;
    privatePostOpenapiFiatV1History(params?: {}): Promise<implicitReturnType>;
    privatePostOpenapiMigrationV4Sellorder(params?: {}): Promise<implicitReturnType>;
    privatePostOpenapiMigrationV4ValidateField(params?: {}): Promise<implicitReturnType>;
    privatePostOpenapiTransferV3Transfers(params?: {}): Promise<implicitReturnType>;
    privateDeleteOpenapiV1Order(params?: {}): Promise<implicitReturnType>;
    privateDeleteOpenapiV1OpenOrders(params?: {}): Promise<implicitReturnType>;
    privateDeleteOpenapiV1UserDataStream(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/coinsph.d.ts`.

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
ts-node js/src/abstract/coinsph.d.ts
```

