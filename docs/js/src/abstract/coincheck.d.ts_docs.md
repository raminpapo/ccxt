# Documentation: js/src/abstract/coincheck.d.ts

## File Metadata

- **Path**: `js/src/abstract/coincheck.d.ts`
- **Size**: 2,370 bytes
- **Lines**: 37
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetExchangeOrdersRate(params?: {}): Promise<implicitReturnType>;
    publicGetOrderBooks(params?: {}): Promise<implicitReturnType>;
    publicGetRatePair(params?: {}): Promise<implicitReturnType>;
    publicGetTicker(params?: {}): Promise<implicitReturnType>;
    publicGetTrades(params?: {}): Promise<implicitReturnType>;
    privateGetAccounts(params?: {}): Promise<implicitReturnType>;
    privateGetAccountsBalance(params?: {}): Promise<implicitReturnType>;
    privateGetAccountsLeverageBalance(params?: {}): Promise<implicitReturnType>;
    privateGetBankAccounts(params?: {}): Promise<implicitReturnType>;
    privateGetDepositMoney(params?: {}): Promise<implicitReturnType>;
    privateGetExchangeOrdersOpens(params?: {}): Promise<implicitReturnType>;
    privateGetExchangeOrdersTransactions(params?: {}): Promise<implicitReturnType>;
    privateGetExchangeOrdersTransactionsPagination(params?: {}): Promise<implicitReturnType>;
    privateGetExchangeLeveragePositions(params?: {}): Promise<implicitReturnType>;
    privateGetLendingBorrowsMatches(params?: {}): Promise<implicitReturnType>;
    privateGetSendMoney(params?: {}): Promise<implicitReturnType>;
    privateGetWithdraws(params?: {}): Promise<implicitReturnType>;
    privatePostBankAccounts(params?: {}): Promise<implicitReturnType>;
    privatePostDepositMoneyIdFast(params?: {}): Promise<implicitReturnType>;
    privatePostExchangeOrders(params?: {}): Promise<implicitReturnType>;
    privatePostExchangeTransfersToLeverage(params?: {}): Promise<implicitReturnType>;
    privatePostExchangeTransfersFromLeverage(params?: {}): Promise<implicitReturnType>;
    privatePostLendingBorrows(params?: {}): Promise<implicitReturnType>;
    privatePostLendingBorrowsIdRepay(params?: {}): Promise<implicitReturnType>;
    privatePostSendMoney(params?: {}): Promise<implicitReturnType>;
    privatePostWithdraws(params?: {}): Promise<implicitReturnType>;
    privateDeleteBankAccountsId(params?: {}): Promise<implicitReturnType>;
    privateDeleteExchangeOrdersId(params?: {}): Promise<implicitReturnType>;
    privateDeleteWithdrawsId(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/coincheck.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 36
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
ts-node js/src/abstract/coincheck.d.ts
```

