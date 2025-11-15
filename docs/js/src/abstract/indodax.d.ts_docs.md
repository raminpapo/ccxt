# Documentation: js/src/abstract/indodax.d.ts

## File Metadata

- **Path**: `js/src/abstract/indodax.d.ts`
- **Size**: 1,757 bytes
- **Lines**: 30
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetApiServerTime(params?: {}): Promise<implicitReturnType>;
    publicGetApiPairs(params?: {}): Promise<implicitReturnType>;
    publicGetApiPriceIncrements(params?: {}): Promise<implicitReturnType>;
    publicGetApiSummaries(params?: {}): Promise<implicitReturnType>;
    publicGetApiTickerPair(params?: {}): Promise<implicitReturnType>;
    publicGetApiTickerAll(params?: {}): Promise<implicitReturnType>;
    publicGetApiTradesPair(params?: {}): Promise<implicitReturnType>;
    publicGetApiDepthPair(params?: {}): Promise<implicitReturnType>;
    publicGetTradingviewHistoryV2(params?: {}): Promise<implicitReturnType>;
    privatePostGetInfo(params?: {}): Promise<implicitReturnType>;
    privatePostTransHistory(params?: {}): Promise<implicitReturnType>;
    privatePostTrade(params?: {}): Promise<implicitReturnType>;
    privatePostTradeHistory(params?: {}): Promise<implicitReturnType>;
    privatePostOpenOrders(params?: {}): Promise<implicitReturnType>;
    privatePostOrderHistory(params?: {}): Promise<implicitReturnType>;
    privatePostGetOrder(params?: {}): Promise<implicitReturnType>;
    privatePostCancelOrder(params?: {}): Promise<implicitReturnType>;
    privatePostWithdrawFee(params?: {}): Promise<implicitReturnType>;
    privatePostWithdrawCoin(params?: {}): Promise<implicitReturnType>;
    privatePostListDownline(params?: {}): Promise<implicitReturnType>;
    privatePostCheckDownline(params?: {}): Promise<implicitReturnType>;
    privatePostCreateVoucher(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/indodax.d.ts`.

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
ts-node js/src/abstract/indodax.d.ts
```

