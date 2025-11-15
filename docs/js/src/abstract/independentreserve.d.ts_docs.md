# Documentation: js/src/abstract/independentreserve.d.ts

## File Metadata

- **Path**: `js/src/abstract/independentreserve.d.ts`
- **Size**: 3,288 bytes
- **Lines**: 47
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetGetValidPrimaryCurrencyCodes(params?: {}): Promise<implicitReturnType>;
    publicGetGetValidSecondaryCurrencyCodes(params?: {}): Promise<implicitReturnType>;
    publicGetGetValidLimitOrderTypes(params?: {}): Promise<implicitReturnType>;
    publicGetGetValidMarketOrderTypes(params?: {}): Promise<implicitReturnType>;
    publicGetGetValidOrderTypes(params?: {}): Promise<implicitReturnType>;
    publicGetGetValidTransactionTypes(params?: {}): Promise<implicitReturnType>;
    publicGetGetMarketSummary(params?: {}): Promise<implicitReturnType>;
    publicGetGetOrderBook(params?: {}): Promise<implicitReturnType>;
    publicGetGetAllOrders(params?: {}): Promise<implicitReturnType>;
    publicGetGetTradeHistorySummary(params?: {}): Promise<implicitReturnType>;
    publicGetGetRecentTrades(params?: {}): Promise<implicitReturnType>;
    publicGetGetFxRates(params?: {}): Promise<implicitReturnType>;
    publicGetGetOrderMinimumVolumes(params?: {}): Promise<implicitReturnType>;
    publicGetGetCryptoWithdrawalFees(params?: {}): Promise<implicitReturnType>;
    publicGetGetCryptoWithdrawalFees2(params?: {}): Promise<implicitReturnType>;
    publicGetGetNetworks(params?: {}): Promise<implicitReturnType>;
    publicGetGetPrimaryCurrencyConfig2(params?: {}): Promise<implicitReturnType>;
    privatePostGetOpenOrders(params?: {}): Promise<implicitReturnType>;
    privatePostGetClosedOrders(params?: {}): Promise<implicitReturnType>;
    privatePostGetClosedFilledOrders(params?: {}): Promise<implicitReturnType>;
    privatePostGetOrderDetails(params?: {}): Promise<implicitReturnType>;
    privatePostGetAccounts(params?: {}): Promise<implicitReturnType>;
    privatePostGetTransactions(params?: {}): Promise<implicitReturnType>;
    privatePostGetFiatBankAccounts(params?: {}): Promise<implicitReturnType>;
    privatePostGetDigitalCurrencyDepositAddress(params?: {}): Promise<implicitReturnType>;
    privatePostGetDigitalCurrencyDepositAddress2(params?: {}): Promise<implicitReturnType>;
    privatePostGetDigitalCurrencyDepositAddresses(params?: {}): Promise<implicitReturnType>;
    privatePostGetDigitalCurrencyDepositAddresses2(params?: {}): Promise<implicitReturnType>;
    privatePostGetTrades(params?: {}): Promise<implicitReturnType>;
    privatePostGetBrokerageFees(params?: {}): Promise<implicitReturnType>;
    privatePostGetDigitalCurrencyWithdrawal(params?: {}): Promise<implicitReturnType>;
    privatePostPlaceLimitOrder(params?: {}): Promise<implicitReturnType>;
    privatePostPlaceMarketOrder(params?: {}): Promise<implicitReturnType>;
    privatePostCancelOrder(params?: {}): Promise<implicitReturnType>;
    privatePostSynchDigitalCurrencyDepositAddressWithBlockchain(params?: {}): Promise<implicitReturnType>;
    privatePostRequestFiatWithdrawal(params?: {}): Promise<implicitReturnType>;
    privatePostWithdrawFiatCurrency(params?: {}): Promise<implicitReturnType>;
    privatePostWithdrawDigitalCurrency(params?: {}): Promise<implicitReturnType>;
    privatePostWithdrawCrypto(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/independentreserve.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 46
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
ts-node js/src/abstract/independentreserve.d.ts
```

