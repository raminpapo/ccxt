# Documentation: js/src/abstract/bithumb.d.ts

## File Metadata

- **Path**: `js/src/abstract/bithumb.d.ts`
- **Size**: 2,332 bytes
- **Lines**: 36
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetTickerALLQuoteId(params?: {}): Promise<implicitReturnType>;
    publicGetTickerBaseIdQuoteId(params?: {}): Promise<implicitReturnType>;
    publicGetOrderbookALLQuoteId(params?: {}): Promise<implicitReturnType>;
    publicGetOrderbookBaseIdQuoteId(params?: {}): Promise<implicitReturnType>;
    publicGetTransactionHistoryBaseIdQuoteId(params?: {}): Promise<implicitReturnType>;
    publicGetNetworkInfo(params?: {}): Promise<implicitReturnType>;
    publicGetAssetsstatusMultichainALL(params?: {}): Promise<implicitReturnType>;
    publicGetAssetsstatusMultichainCurrency(params?: {}): Promise<implicitReturnType>;
    publicGetWithdrawMinimumALL(params?: {}): Promise<implicitReturnType>;
    publicGetWithdrawMinimumCurrency(params?: {}): Promise<implicitReturnType>;
    publicGetAssetsstatusALL(params?: {}): Promise<implicitReturnType>;
    publicGetAssetsstatusBaseId(params?: {}): Promise<implicitReturnType>;
    publicGetCandlestickBaseIdQuoteIdInterval(params?: {}): Promise<implicitReturnType>;
    privatePostInfoAccount(params?: {}): Promise<implicitReturnType>;
    privatePostInfoBalance(params?: {}): Promise<implicitReturnType>;
    privatePostInfoWalletAddress(params?: {}): Promise<implicitReturnType>;
    privatePostInfoTicker(params?: {}): Promise<implicitReturnType>;
    privatePostInfoOrders(params?: {}): Promise<implicitReturnType>;
    privatePostInfoUserTransactions(params?: {}): Promise<implicitReturnType>;
    privatePostInfoOrderDetail(params?: {}): Promise<implicitReturnType>;
    privatePostTradePlace(params?: {}): Promise<implicitReturnType>;
    privatePostTradeCancel(params?: {}): Promise<implicitReturnType>;
    privatePostTradeBtcWithdrawal(params?: {}): Promise<implicitReturnType>;
    privatePostTradeKrwDeposit(params?: {}): Promise<implicitReturnType>;
    privatePostTradeKrwWithdrawal(params?: {}): Promise<implicitReturnType>;
    privatePostTradeMarketBuy(params?: {}): Promise<implicitReturnType>;
    privatePostTradeMarketSell(params?: {}): Promise<implicitReturnType>;
    privatePostTradeStopLimit(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/bithumb.d.ts`.

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
ts-node js/src/abstract/bithumb.d.ts
```

