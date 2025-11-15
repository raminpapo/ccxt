# Documentation: js/src/abstract/hibachi.d.ts

## File Metadata

- **Path**: `js/src/abstract/hibachi.d.ts`
- **Size**: 1,838 bytes
- **Lines**: 30
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetMarketExchangeInfo(params?: {}): Promise<implicitReturnType>;
    publicGetMarketDataTrades(params?: {}): Promise<implicitReturnType>;
    publicGetMarketDataPrices(params?: {}): Promise<implicitReturnType>;
    publicGetMarketDataStats(params?: {}): Promise<implicitReturnType>;
    publicGetMarketDataKlines(params?: {}): Promise<implicitReturnType>;
    publicGetMarketDataOrderbook(params?: {}): Promise<implicitReturnType>;
    publicGetMarketDataOpenInterest(params?: {}): Promise<implicitReturnType>;
    publicGetMarketDataFundingRates(params?: {}): Promise<implicitReturnType>;
    publicGetExchangeUtcTimestamp(params?: {}): Promise<implicitReturnType>;
    privateGetCapitalDepositInfo(params?: {}): Promise<implicitReturnType>;
    privateGetCapitalHistory(params?: {}): Promise<implicitReturnType>;
    privateGetTradeAccountTradingHistory(params?: {}): Promise<implicitReturnType>;
    privateGetTradeAccountInfo(params?: {}): Promise<implicitReturnType>;
    privateGetTradeOrder(params?: {}): Promise<implicitReturnType>;
    privateGetTradeAccountTrades(params?: {}): Promise<implicitReturnType>;
    privateGetTradeOrders(params?: {}): Promise<implicitReturnType>;
    privatePutTradeOrder(params?: {}): Promise<implicitReturnType>;
    privateDeleteTradeOrder(params?: {}): Promise<implicitReturnType>;
    privateDeleteTradeOrders(params?: {}): Promise<implicitReturnType>;
    privatePostTradeOrder(params?: {}): Promise<implicitReturnType>;
    privatePostTradeOrders(params?: {}): Promise<implicitReturnType>;
    privatePostCapitalWithdraw(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/hibachi.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 29
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
ts-node js/src/abstract/hibachi.d.ts
```

