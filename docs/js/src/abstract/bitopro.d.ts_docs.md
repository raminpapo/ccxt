# Documentation: js/src/abstract/bitopro.d.ts

## File Metadata

- **Path**: `js/src/abstract/bitopro.d.ts`
- **Size**: 2,155 bytes
- **Lines**: 34
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetOrderBookPair(params?: {}): Promise<implicitReturnType>;
    publicGetTickers(params?: {}): Promise<implicitReturnType>;
    publicGetTickersPair(params?: {}): Promise<implicitReturnType>;
    publicGetTradesPair(params?: {}): Promise<implicitReturnType>;
    publicGetProvisioningCurrencies(params?: {}): Promise<implicitReturnType>;
    publicGetProvisioningTradingPairs(params?: {}): Promise<implicitReturnType>;
    publicGetProvisioningLimitationsAndFees(params?: {}): Promise<implicitReturnType>;
    publicGetTradingHistoryPair(params?: {}): Promise<implicitReturnType>;
    publicGetPriceOtcCurrency(params?: {}): Promise<implicitReturnType>;
    privateGetAccountsBalance(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersHistory(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersAllPair(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersTradesPair(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersPairOrderId(params?: {}): Promise<implicitReturnType>;
    privateGetWalletWithdrawCurrencySerial(params?: {}): Promise<implicitReturnType>;
    privateGetWalletWithdrawCurrencyIdId(params?: {}): Promise<implicitReturnType>;
    privateGetWalletDepositHistoryCurrency(params?: {}): Promise<implicitReturnType>;
    privateGetWalletWithdrawHistoryCurrency(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersOpen(params?: {}): Promise<implicitReturnType>;
    privatePostOrdersPair(params?: {}): Promise<implicitReturnType>;
    privatePostOrdersBatch(params?: {}): Promise<implicitReturnType>;
    privatePostWalletWithdrawCurrency(params?: {}): Promise<implicitReturnType>;
    privatePutOrders(params?: {}): Promise<implicitReturnType>;
    privateDeleteOrdersPairId(params?: {}): Promise<implicitReturnType>;
    privateDeleteOrdersAll(params?: {}): Promise<implicitReturnType>;
    privateDeleteOrdersPair(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/bitopro.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 33
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
ts-node js/src/abstract/bitopro.d.ts
```

