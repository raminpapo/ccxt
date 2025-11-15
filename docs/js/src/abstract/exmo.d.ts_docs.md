# Documentation: js/src/abstract/exmo.d.ts

## File Metadata

- **Path**: `js/src/abstract/exmo.d.ts`
- **Size**: 4,060 bytes
- **Lines**: 59
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    webGetCtrlFeesAndLimits(params?: {}): Promise<implicitReturnType>;
    webGetEnDocsFees(params?: {}): Promise<implicitReturnType>;
    publicGetCurrency(params?: {}): Promise<implicitReturnType>;
    publicGetCurrencyListExtended(params?: {}): Promise<implicitReturnType>;
    publicGetOrderBook(params?: {}): Promise<implicitReturnType>;
    publicGetPairSettings(params?: {}): Promise<implicitReturnType>;
    publicGetTicker(params?: {}): Promise<implicitReturnType>;
    publicGetTrades(params?: {}): Promise<implicitReturnType>;
    publicGetCandlesHistory(params?: {}): Promise<implicitReturnType>;
    publicGetRequiredAmount(params?: {}): Promise<implicitReturnType>;
    publicGetPaymentsProvidersCryptoList(params?: {}): Promise<implicitReturnType>;
    privatePostUserInfo(params?: {}): Promise<implicitReturnType>;
    privatePostOrderCreate(params?: {}): Promise<implicitReturnType>;
    privatePostOrderCancel(params?: {}): Promise<implicitReturnType>;
    privatePostStopMarketOrderCreate(params?: {}): Promise<implicitReturnType>;
    privatePostStopMarketOrderCancel(params?: {}): Promise<implicitReturnType>;
    privatePostUserOpenOrders(params?: {}): Promise<implicitReturnType>;
    privatePostUserTrades(params?: {}): Promise<implicitReturnType>;
    privatePostUserCancelledOrders(params?: {}): Promise<implicitReturnType>;
    privatePostOrderTrades(params?: {}): Promise<implicitReturnType>;
    privatePostDepositAddress(params?: {}): Promise<implicitReturnType>;
    privatePostWithdrawCrypt(params?: {}): Promise<implicitReturnType>;
    privatePostWithdrawGetTxid(params?: {}): Promise<implicitReturnType>;
    privatePostExcodeCreate(params?: {}): Promise<implicitReturnType>;
    privatePostExcodeLoad(params?: {}): Promise<implicitReturnType>;
    privatePostCodeCheck(params?: {}): Promise<implicitReturnType>;
    privatePostWalletHistory(params?: {}): Promise<implicitReturnType>;
    privatePostWalletOperations(params?: {}): Promise<implicitReturnType>;
    privatePostMarginUserOrderCreate(params?: {}): Promise<implicitReturnType>;
    privatePostMarginUserOrderUpdate(params?: {}): Promise<implicitReturnType>;
    privatePostMarginUserOrderCancel(params?: {}): Promise<implicitReturnType>;
    privatePostMarginUserPositionClose(params?: {}): Promise<implicitReturnType>;
    privatePostMarginUserPositionMarginAdd(params?: {}): Promise<implicitReturnType>;
    privatePostMarginUserPositionMarginRemove(params?: {}): Promise<implicitReturnType>;
    privatePostMarginCurrencyList(params?: {}): Promise<implicitReturnType>;
    privatePostMarginPairList(params?: {}): Promise<implicitReturnType>;
    privatePostMarginSettings(params?: {}): Promise<implicitReturnType>;
    privatePostMarginFundingList(params?: {}): Promise<implicitReturnType>;
    privatePostMarginUserInfo(params?: {}): Promise<implicitReturnType>;
    privatePostMarginUserOrderList(params?: {}): Promise<implicitReturnType>;
    privatePostMarginUserOrderHistory(params?: {}): Promise<implicitReturnType>;
    privatePostMarginUserOrderTrades(params?: {}): Promise<implicitReturnType>;
    privatePostMarginUserOrderMaxQuantity(params?: {}): Promise<implicitReturnType>;
    privatePostMarginUserPositionList(params?: {}): Promise<implicitReturnType>;
    privatePostMarginUserPositionMarginRemoveInfo(params?: {}): Promise<implicitReturnType>;
    privatePostMarginUserPositionMarginAddInfo(params?: {}): Promise<implicitReturnType>;
    privatePostMarginUserWalletList(params?: {}): Promise<implicitReturnType>;
    privatePostMarginUserWalletHistory(params?: {}): Promise<implicitReturnType>;
    privatePostMarginUserTradeList(params?: {}): Promise<implicitReturnType>;
    privatePostMarginTrades(params?: {}): Promise<implicitReturnType>;
    privatePostMarginLiquidationFeed(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/exmo.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 59
- Code lines: 58
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
ts-node js/src/abstract/exmo.d.ts
```

