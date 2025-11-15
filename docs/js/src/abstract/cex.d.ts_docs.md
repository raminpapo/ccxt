# Documentation: js/src/abstract/cex.d.ts

## File Metadata

- **Path**: `js/src/abstract/cex.d.ts`
- **Size**: 2,297 bytes
- **Lines**: 36
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicPostGetServerTime(params?: {}): Promise<implicitReturnType>;
    publicPostGetPairsInfo(params?: {}): Promise<implicitReturnType>;
    publicPostGetCurrenciesInfo(params?: {}): Promise<implicitReturnType>;
    publicPostGetProcessingInfo(params?: {}): Promise<implicitReturnType>;
    publicPostGetTicker(params?: {}): Promise<implicitReturnType>;
    publicPostGetTradeHistory(params?: {}): Promise<implicitReturnType>;
    publicPostGetOrderBook(params?: {}): Promise<implicitReturnType>;
    publicPostGetCandles(params?: {}): Promise<implicitReturnType>;
    privatePostGetMyCurrentFee(params?: {}): Promise<implicitReturnType>;
    privatePostGetFeeStrategy(params?: {}): Promise<implicitReturnType>;
    privatePostGetMyVolume(params?: {}): Promise<implicitReturnType>;
    privatePostDoCreateAccount(params?: {}): Promise<implicitReturnType>;
    privatePostGetMyAccountStatusV3(params?: {}): Promise<implicitReturnType>;
    privatePostGetMyWalletBalance(params?: {}): Promise<implicitReturnType>;
    privatePostGetMyOrders(params?: {}): Promise<implicitReturnType>;
    privatePostDoMyNewOrder(params?: {}): Promise<implicitReturnType>;
    privatePostDoCancelMyOrder(params?: {}): Promise<implicitReturnType>;
    privatePostDoCancelAllOrders(params?: {}): Promise<implicitReturnType>;
    privatePostGetOrderBook(params?: {}): Promise<implicitReturnType>;
    privatePostGetCandles(params?: {}): Promise<implicitReturnType>;
    privatePostGetTradeHistory(params?: {}): Promise<implicitReturnType>;
    privatePostGetMyTransactionHistory(params?: {}): Promise<implicitReturnType>;
    privatePostGetMyFundingHistory(params?: {}): Promise<implicitReturnType>;
    privatePostDoMyInternalTransfer(params?: {}): Promise<implicitReturnType>;
    privatePostGetProcessingInfo(params?: {}): Promise<implicitReturnType>;
    privatePostGetDepositAddress(params?: {}): Promise<implicitReturnType>;
    privatePostDoDepositFundsFromWallet(params?: {}): Promise<implicitReturnType>;
    privatePostDoWithdrawalFundsToWallet(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/cex.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 35
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
ts-node js/src/abstract/cex.d.ts
```

