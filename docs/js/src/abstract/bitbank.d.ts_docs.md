# Documentation: js/src/abstract/bitbank.d.ts

## File Metadata

- **Path**: `js/src/abstract/bitbank.d.ts`
- **Size**: 2,317 bytes
- **Lines**: 36
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetPairTicker(params?: {}): Promise<implicitReturnType>;
    publicGetTickers(params?: {}): Promise<implicitReturnType>;
    publicGetTickersJpy(params?: {}): Promise<implicitReturnType>;
    publicGetPairDepth(params?: {}): Promise<implicitReturnType>;
    publicGetPairTransactions(params?: {}): Promise<implicitReturnType>;
    publicGetPairTransactionsYyyymmdd(params?: {}): Promise<implicitReturnType>;
    publicGetPairCandlestickCandletypeYyyymmdd(params?: {}): Promise<implicitReturnType>;
    publicGetPairCircuitBreakInfo(params?: {}): Promise<implicitReturnType>;
    privateGetUserAssets(params?: {}): Promise<implicitReturnType>;
    privateGetUserSpotOrder(params?: {}): Promise<implicitReturnType>;
    privateGetUserSpotActiveOrders(params?: {}): Promise<implicitReturnType>;
    privateGetUserMarginPositions(params?: {}): Promise<implicitReturnType>;
    privateGetUserSpotTradeHistory(params?: {}): Promise<implicitReturnType>;
    privateGetUserDepositHistory(params?: {}): Promise<implicitReturnType>;
    privateGetUserUnconfirmedDeposits(params?: {}): Promise<implicitReturnType>;
    privateGetUserDepositOriginators(params?: {}): Promise<implicitReturnType>;
    privateGetUserWithdrawalAccount(params?: {}): Promise<implicitReturnType>;
    privateGetUserWithdrawalHistory(params?: {}): Promise<implicitReturnType>;
    privateGetSpotStatus(params?: {}): Promise<implicitReturnType>;
    privateGetSpotPairs(params?: {}): Promise<implicitReturnType>;
    privatePostUserSpotOrder(params?: {}): Promise<implicitReturnType>;
    privatePostUserSpotCancelOrder(params?: {}): Promise<implicitReturnType>;
    privatePostUserSpotCancelOrders(params?: {}): Promise<implicitReturnType>;
    privatePostUserSpotOrdersInfo(params?: {}): Promise<implicitReturnType>;
    privatePostUserConfirmDeposits(params?: {}): Promise<implicitReturnType>;
    privatePostUserConfirmDepositsAll(params?: {}): Promise<implicitReturnType>;
    privatePostUserRequestWithdrawal(params?: {}): Promise<implicitReturnType>;
    marketsGetSpotPairs(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/bitbank.d.ts`.

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
ts-node js/src/abstract/bitbank.d.ts
```

