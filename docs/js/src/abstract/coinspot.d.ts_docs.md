# Documentation: js/src/abstract/coinspot.d.ts

## File Metadata

- **Path**: `js/src/abstract/coinspot.d.ts`
- **Size**: 1,952 bytes
- **Lines**: 32
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetLatest(params?: {}): Promise<implicitReturnType>;
    privatePostOrders(params?: {}): Promise<implicitReturnType>;
    privatePostOrdersHistory(params?: {}): Promise<implicitReturnType>;
    privatePostMyCoinDeposit(params?: {}): Promise<implicitReturnType>;
    privatePostMyCoinSend(params?: {}): Promise<implicitReturnType>;
    privatePostQuoteBuy(params?: {}): Promise<implicitReturnType>;
    privatePostQuoteSell(params?: {}): Promise<implicitReturnType>;
    privatePostMyBalances(params?: {}): Promise<implicitReturnType>;
    privatePostMyOrders(params?: {}): Promise<implicitReturnType>;
    privatePostMyBuy(params?: {}): Promise<implicitReturnType>;
    privatePostMySell(params?: {}): Promise<implicitReturnType>;
    privatePostMyBuyCancel(params?: {}): Promise<implicitReturnType>;
    privatePostMySellCancel(params?: {}): Promise<implicitReturnType>;
    privatePostRoMyBalances(params?: {}): Promise<implicitReturnType>;
    privatePostRoMyBalancesCointype(params?: {}): Promise<implicitReturnType>;
    privatePostRoMyDeposits(params?: {}): Promise<implicitReturnType>;
    privatePostRoMyWithdrawals(params?: {}): Promise<implicitReturnType>;
    privatePostRoMyTransactions(params?: {}): Promise<implicitReturnType>;
    privatePostRoMyTransactionsCointype(params?: {}): Promise<implicitReturnType>;
    privatePostRoMyTransactionsOpen(params?: {}): Promise<implicitReturnType>;
    privatePostRoMyTransactionsCointypeOpen(params?: {}): Promise<implicitReturnType>;
    privatePostRoMySendreceive(params?: {}): Promise<implicitReturnType>;
    privatePostRoMyAffiliatepayments(params?: {}): Promise<implicitReturnType>;
    privatePostRoMyReferralpayments(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/coinspot.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 31
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
ts-node js/src/abstract/coinspot.d.ts
```

