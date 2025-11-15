# Documentation: js/src/abstract/bitteam.d.ts

## File Metadata

- **Path**: `js/src/abstract/bitteam.d.ts`
- **Size**: 2,146 bytes
- **Lines**: 33
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    historyGetApiTwHistoryPairNameResolution(params?: {}): Promise<implicitReturnType>;
    publicGetTradeApiAsset(params?: {}): Promise<implicitReturnType>;
    publicGetTradeApiCurrencies(params?: {}): Promise<implicitReturnType>;
    publicGetTradeApiOrderbooksSymbol(params?: {}): Promise<implicitReturnType>;
    publicGetTradeApiOrders(params?: {}): Promise<implicitReturnType>;
    publicGetTradeApiPairName(params?: {}): Promise<implicitReturnType>;
    publicGetTradeApiPairs(params?: {}): Promise<implicitReturnType>;
    publicGetTradeApiPairsPrecisions(params?: {}): Promise<implicitReturnType>;
    publicGetTradeApiRates(params?: {}): Promise<implicitReturnType>;
    publicGetTradeApiTradeId(params?: {}): Promise<implicitReturnType>;
    publicGetTradeApiTrades(params?: {}): Promise<implicitReturnType>;
    publicGetTradeApiCcxtPairs(params?: {}): Promise<implicitReturnType>;
    publicGetTradeApiCmcAssets(params?: {}): Promise<implicitReturnType>;
    publicGetTradeApiCmcOrderbookPair(params?: {}): Promise<implicitReturnType>;
    publicGetTradeApiCmcSummary(params?: {}): Promise<implicitReturnType>;
    publicGetTradeApiCmcTicker(params?: {}): Promise<implicitReturnType>;
    publicGetTradeApiCmcTradesPair(params?: {}): Promise<implicitReturnType>;
    privateGetTradeApiCcxtBalance(params?: {}): Promise<implicitReturnType>;
    privateGetTradeApiCcxtOrderId(params?: {}): Promise<implicitReturnType>;
    privateGetTradeApiCcxtOrdersOfUser(params?: {}): Promise<implicitReturnType>;
    privateGetTradeApiCcxtTradesOfUser(params?: {}): Promise<implicitReturnType>;
    privateGetTradeApiTransactionsOfUser(params?: {}): Promise<implicitReturnType>;
    privatePostTradeApiCcxtCancelAllOrder(params?: {}): Promise<implicitReturnType>;
    privatePostTradeApiCcxtCancelorder(params?: {}): Promise<implicitReturnType>;
    privatePostTradeApiCcxtOrdercreate(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/bitteam.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 32
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
ts-node js/src/abstract/bitteam.d.ts
```

