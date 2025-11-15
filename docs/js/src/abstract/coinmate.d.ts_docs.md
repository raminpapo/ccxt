# Documentation: js/src/abstract/coinmate.d.ts

## File Metadata

- **Path**: `js/src/abstract/coinmate.d.ts`
- **Size**: 4,607 bytes
- **Lines**: 66
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetOrderBook(params?: {}): Promise<implicitReturnType>;
    publicGetTicker(params?: {}): Promise<implicitReturnType>;
    publicGetTickerAll(params?: {}): Promise<implicitReturnType>;
    publicGetProducts(params?: {}): Promise<implicitReturnType>;
    publicGetTransactions(params?: {}): Promise<implicitReturnType>;
    publicGetTradingPairs(params?: {}): Promise<implicitReturnType>;
    privatePostBalances(params?: {}): Promise<implicitReturnType>;
    privatePostBitcoinCashWithdrawal(params?: {}): Promise<implicitReturnType>;
    privatePostBitcoinCashDepositAddresses(params?: {}): Promise<implicitReturnType>;
    privatePostBitcoinDepositAddresses(params?: {}): Promise<implicitReturnType>;
    privatePostBitcoinWithdrawal(params?: {}): Promise<implicitReturnType>;
    privatePostBitcoinWithdrawalFees(params?: {}): Promise<implicitReturnType>;
    privatePostBuyInstant(params?: {}): Promise<implicitReturnType>;
    privatePostBuyLimit(params?: {}): Promise<implicitReturnType>;
    privatePostCancelOrder(params?: {}): Promise<implicitReturnType>;
    privatePostCancelOrderWithInfo(params?: {}): Promise<implicitReturnType>;
    privatePostCreateVoucher(params?: {}): Promise<implicitReturnType>;
    privatePostDashDepositAddresses(params?: {}): Promise<implicitReturnType>;
    privatePostDashWithdrawal(params?: {}): Promise<implicitReturnType>;
    privatePostEthereumWithdrawal(params?: {}): Promise<implicitReturnType>;
    privatePostEthereumDepositAddresses(params?: {}): Promise<implicitReturnType>;
    privatePostLitecoinWithdrawal(params?: {}): Promise<implicitReturnType>;
    privatePostLitecoinDepositAddresses(params?: {}): Promise<implicitReturnType>;
    privatePostOpenOrders(params?: {}): Promise<implicitReturnType>;
    privatePostOrder(params?: {}): Promise<implicitReturnType>;
    privatePostOrderHistory(params?: {}): Promise<implicitReturnType>;
    privatePostOrderById(params?: {}): Promise<implicitReturnType>;
    privatePostPusherAuth(params?: {}): Promise<implicitReturnType>;
    privatePostRedeemVoucher(params?: {}): Promise<implicitReturnType>;
    privatePostReplaceByBuyLimit(params?: {}): Promise<implicitReturnType>;
    privatePostReplaceByBuyInstant(params?: {}): Promise<implicitReturnType>;
    privatePostReplaceBySellLimit(params?: {}): Promise<implicitReturnType>;
    privatePostReplaceBySellInstant(params?: {}): Promise<implicitReturnType>;
    privatePostRippleDepositAddresses(params?: {}): Promise<implicitReturnType>;
    privatePostRippleWithdrawal(params?: {}): Promise<implicitReturnType>;
    privatePostSellInstant(params?: {}): Promise<implicitReturnType>;
    privatePostSellLimit(params?: {}): Promise<implicitReturnType>;
    privatePostTransactionHistory(params?: {}): Promise<implicitReturnType>;
    privatePostTraderFees(params?: {}): Promise<implicitReturnType>;
    privatePostTradeHistory(params?: {}): Promise<implicitReturnType>;
    privatePostTransfer(params?: {}): Promise<implicitReturnType>;
    privatePostTransferHistory(params?: {}): Promise<implicitReturnType>;
    privatePostUnconfirmedBitcoinDeposits(params?: {}): Promise<implicitReturnType>;
    privatePostUnconfirmedBitcoinCashDeposits(params?: {}): Promise<implicitReturnType>;
    privatePostUnconfirmedDashDeposits(params?: {}): Promise<implicitReturnType>;
    privatePostUnconfirmedEthereumDeposits(params?: {}): Promise<implicitReturnType>;
    privatePostUnconfirmedLitecoinDeposits(params?: {}): Promise<implicitReturnType>;
    privatePostUnconfirmedRippleDeposits(params?: {}): Promise<implicitReturnType>;
    privatePostCancelAllOpenOrders(params?: {}): Promise<implicitReturnType>;
    privatePostWithdrawVirtualCurrency(params?: {}): Promise<implicitReturnType>;
    privatePostVirtualCurrencyDepositAddresses(params?: {}): Promise<implicitReturnType>;
    privatePostUnconfirmedVirtualCurrencyDeposits(params?: {}): Promise<implicitReturnType>;
    privatePostAdaWithdrawal(params?: {}): Promise<implicitReturnType>;
    privatePostAdaDepositAddresses(params?: {}): Promise<implicitReturnType>;
    privatePostUnconfirmedAdaDeposits(params?: {}): Promise<implicitReturnType>;
    privatePostSolWithdrawal(params?: {}): Promise<implicitReturnType>;
    privatePostSolDepositAddresses(params?: {}): Promise<implicitReturnType>;
    privatePostUnconfirmedSolDeposits(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/coinmate.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 66
- Code lines: 65
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
ts-node js/src/abstract/coinmate.d.ts
```

