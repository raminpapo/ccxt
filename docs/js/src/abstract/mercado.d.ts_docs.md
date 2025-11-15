# Documentation: js/src/abstract/mercado.d.ts

## File Metadata

- **Path**: `js/src/abstract/mercado.d.ts`
- **Size**: 1,722 bytes
- **Lines**: 29
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetCoins(params?: {}): Promise<implicitReturnType>;
    publicGetCoinOrderbook(params?: {}): Promise<implicitReturnType>;
    publicGetCoinTicker(params?: {}): Promise<implicitReturnType>;
    publicGetCoinTrades(params?: {}): Promise<implicitReturnType>;
    publicGetCoinTradesFrom(params?: {}): Promise<implicitReturnType>;
    publicGetCoinTradesFromTo(params?: {}): Promise<implicitReturnType>;
    publicGetCoinDaySummaryYearMonthDay(params?: {}): Promise<implicitReturnType>;
    privatePostCancelOrder(params?: {}): Promise<implicitReturnType>;
    privatePostGetAccountInfo(params?: {}): Promise<implicitReturnType>;
    privatePostGetOrder(params?: {}): Promise<implicitReturnType>;
    privatePostGetWithdrawal(params?: {}): Promise<implicitReturnType>;
    privatePostListSystemMessages(params?: {}): Promise<implicitReturnType>;
    privatePostListOrders(params?: {}): Promise<implicitReturnType>;
    privatePostListOrderbook(params?: {}): Promise<implicitReturnType>;
    privatePostPlaceBuyOrder(params?: {}): Promise<implicitReturnType>;
    privatePostPlaceSellOrder(params?: {}): Promise<implicitReturnType>;
    privatePostPlaceMarketBuyOrder(params?: {}): Promise<implicitReturnType>;
    privatePostPlaceMarketSellOrder(params?: {}): Promise<implicitReturnType>;
    privatePostWithdrawCoin(params?: {}): Promise<implicitReturnType>;
    v4PublicGetCoinCandle(params?: {}): Promise<implicitReturnType>;
    v4PublicNetGetCandles(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/mercado.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 28
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
ts-node js/src/abstract/mercado.d.ts
```

