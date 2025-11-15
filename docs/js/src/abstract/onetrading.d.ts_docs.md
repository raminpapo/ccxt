# Documentation: js/src/abstract/onetrading.d.ts

## File Metadata

- **Path**: `js/src/abstract/onetrading.d.ts`
- **Size**: 1,629 bytes
- **Lines**: 27
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetCurrencies(params?: {}): Promise<implicitReturnType>;
    publicGetCandlesticksInstrumentCode(params?: {}): Promise<implicitReturnType>;
    publicGetFees(params?: {}): Promise<implicitReturnType>;
    publicGetInstruments(params?: {}): Promise<implicitReturnType>;
    publicGetOrderBookInstrumentCode(params?: {}): Promise<implicitReturnType>;
    publicGetMarketTicker(params?: {}): Promise<implicitReturnType>;
    publicGetMarketTickerInstrumentCode(params?: {}): Promise<implicitReturnType>;
    publicGetTime(params?: {}): Promise<implicitReturnType>;
    privateGetAccountBalances(params?: {}): Promise<implicitReturnType>;
    privateGetAccountFees(params?: {}): Promise<implicitReturnType>;
    privateGetAccountOrders(params?: {}): Promise<implicitReturnType>;
    privateGetAccountOrdersOrderId(params?: {}): Promise<implicitReturnType>;
    privateGetAccountOrdersOrderIdTrades(params?: {}): Promise<implicitReturnType>;
    privateGetAccountTrades(params?: {}): Promise<implicitReturnType>;
    privateGetAccountTradesTradeId(params?: {}): Promise<implicitReturnType>;
    privatePostAccountOrders(params?: {}): Promise<implicitReturnType>;
    privateDeleteAccountOrders(params?: {}): Promise<implicitReturnType>;
    privateDeleteAccountOrdersOrderId(params?: {}): Promise<implicitReturnType>;
    privateDeleteAccountOrdersClientClientId(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/onetrading.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 26
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
ts-node js/src/abstract/onetrading.d.ts
```

