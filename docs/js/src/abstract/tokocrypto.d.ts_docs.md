# Documentation: js/src/abstract/tokocrypto.d.ts

## File Metadata

- **Path**: `js/src/abstract/tokocrypto.d.ts`
- **Size**: 2,602 bytes
- **Lines**: 41
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    binanceGetPing(params?: {}): Promise<implicitReturnType>;
    binanceGetTime(params?: {}): Promise<implicitReturnType>;
    binanceGetDepth(params?: {}): Promise<implicitReturnType>;
    binanceGetTrades(params?: {}): Promise<implicitReturnType>;
    binanceGetAggTrades(params?: {}): Promise<implicitReturnType>;
    binanceGetHistoricalTrades(params?: {}): Promise<implicitReturnType>;
    binanceGetKlines(params?: {}): Promise<implicitReturnType>;
    binanceGetTicker24hr(params?: {}): Promise<implicitReturnType>;
    binanceGetTickerPrice(params?: {}): Promise<implicitReturnType>;
    binanceGetTickerBookTicker(params?: {}): Promise<implicitReturnType>;
    binanceGetExchangeInfo(params?: {}): Promise<implicitReturnType>;
    binancePutUserDataStream(params?: {}): Promise<implicitReturnType>;
    binancePostUserDataStream(params?: {}): Promise<implicitReturnType>;
    binanceDeleteUserDataStream(params?: {}): Promise<implicitReturnType>;
    publicGetOpenV1CommonTime(params?: {}): Promise<implicitReturnType>;
    publicGetOpenV1CommonSymbols(params?: {}): Promise<implicitReturnType>;
    publicGetOpenV1MarketDepth(params?: {}): Promise<implicitReturnType>;
    publicGetOpenV1MarketTrades(params?: {}): Promise<implicitReturnType>;
    publicGetOpenV1MarketAggTrades(params?: {}): Promise<implicitReturnType>;
    publicGetOpenV1MarketKlines(params?: {}): Promise<implicitReturnType>;
    privateGetOpenV1OrdersDetail(params?: {}): Promise<implicitReturnType>;
    privateGetOpenV1Orders(params?: {}): Promise<implicitReturnType>;
    privateGetOpenV1AccountSpot(params?: {}): Promise<implicitReturnType>;
    privateGetOpenV1AccountSpotAsset(params?: {}): Promise<implicitReturnType>;
    privateGetOpenV1OrdersTrades(params?: {}): Promise<implicitReturnType>;
    privateGetOpenV1Withdraws(params?: {}): Promise<implicitReturnType>;
    privateGetOpenV1Deposits(params?: {}): Promise<implicitReturnType>;
    privateGetOpenV1DepositsAddress(params?: {}): Promise<implicitReturnType>;
    privatePostOpenV1Orders(params?: {}): Promise<implicitReturnType>;
    privatePostOpenV1OrdersCancel(params?: {}): Promise<implicitReturnType>;
    privatePostOpenV1OrdersOco(params?: {}): Promise<implicitReturnType>;
    privatePostOpenV1Withdraws(params?: {}): Promise<implicitReturnType>;
    privatePostOpenV1UserDataStream(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/tokocrypto.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 40
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
ts-node js/src/abstract/tokocrypto.d.ts
```

