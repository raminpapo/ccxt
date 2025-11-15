# Documentation: js/src/abstract/bit2c.d.ts

## File Metadata

- **Path**: `js/src/abstract/bit2c.d.ts`
- **Size**: 1,965 bytes
- **Lines**: 31
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetExchangesPairTicker(params?: {}): Promise<implicitReturnType>;
    publicGetExchangesPairOrderbook(params?: {}): Promise<implicitReturnType>;
    publicGetExchangesPairTrades(params?: {}): Promise<implicitReturnType>;
    publicGetExchangesPairLasttrades(params?: {}): Promise<implicitReturnType>;
    privatePostMerchantCreateCheckout(params?: {}): Promise<implicitReturnType>;
    privatePostFundsAddCoinFundsRequest(params?: {}): Promise<implicitReturnType>;
    privatePostOrderAddFund(params?: {}): Promise<implicitReturnType>;
    privatePostOrderAddOrder(params?: {}): Promise<implicitReturnType>;
    privatePostOrderGetById(params?: {}): Promise<implicitReturnType>;
    privatePostOrderAddOrderMarketPriceBuy(params?: {}): Promise<implicitReturnType>;
    privatePostOrderAddOrderMarketPriceSell(params?: {}): Promise<implicitReturnType>;
    privatePostOrderCancelOrder(params?: {}): Promise<implicitReturnType>;
    privatePostOrderAddCoinFundsRequest(params?: {}): Promise<implicitReturnType>;
    privatePostOrderAddStopOrder(params?: {}): Promise<implicitReturnType>;
    privatePostPaymentGetMyId(params?: {}): Promise<implicitReturnType>;
    privatePostPaymentSend(params?: {}): Promise<implicitReturnType>;
    privatePostPaymentPay(params?: {}): Promise<implicitReturnType>;
    privateGetAccountBalance(params?: {}): Promise<implicitReturnType>;
    privateGetAccountBalanceV2(params?: {}): Promise<implicitReturnType>;
    privateGetOrderMyOrders(params?: {}): Promise<implicitReturnType>;
    privateGetOrderGetById(params?: {}): Promise<implicitReturnType>;
    privateGetOrderAccountHistory(params?: {}): Promise<implicitReturnType>;
    privateGetOrderOrderHistory(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/bit2c.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 30
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
ts-node js/src/abstract/bit2c.d.ts
```

