# Documentation: js/src/abstract/cryptomus.d.ts

## File Metadata

- **Path**: `js/src/abstract/cryptomus.d.ts`
- **Size**: 1,581 bytes
- **Lines**: 24
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetV2UserApiExchangeMarkets(params?: {}): Promise<implicitReturnType>;
    publicGetV2UserApiExchangeMarketPrice(params?: {}): Promise<implicitReturnType>;
    publicGetV1ExchangeMarketAssets(params?: {}): Promise<implicitReturnType>;
    publicGetV1ExchangeMarketOrderBookCurrencyPair(params?: {}): Promise<implicitReturnType>;
    publicGetV1ExchangeMarketTickers(params?: {}): Promise<implicitReturnType>;
    publicGetV1ExchangeMarketTradesCurrencyPair(params?: {}): Promise<implicitReturnType>;
    privateGetV2UserApiExchangeOrders(params?: {}): Promise<implicitReturnType>;
    privateGetV2UserApiExchangeOrdersHistory(params?: {}): Promise<implicitReturnType>;
    privateGetV2UserApiExchangeAccountBalance(params?: {}): Promise<implicitReturnType>;
    privateGetV2UserApiExchangeAccountTariffs(params?: {}): Promise<implicitReturnType>;
    privateGetV2UserApiPaymentServices(params?: {}): Promise<implicitReturnType>;
    privateGetV2UserApiPayoutServices(params?: {}): Promise<implicitReturnType>;
    privateGetV2UserApiTransactionList(params?: {}): Promise<implicitReturnType>;
    privatePostV2UserApiExchangeOrders(params?: {}): Promise<implicitReturnType>;
    privatePostV2UserApiExchangeOrdersMarket(params?: {}): Promise<implicitReturnType>;
    privateDeleteV2UserApiExchangeOrdersOrderId(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/cryptomus.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 24
- Code lines: 23
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
ts-node js/src/abstract/cryptomus.d.ts
```

