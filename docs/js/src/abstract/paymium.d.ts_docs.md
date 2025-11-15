# Documentation: js/src/abstract/paymium.d.ts

## File Metadata

- **Path**: `js/src/abstract/paymium.d.ts`
- **Size**: 1,992 bytes
- **Lines**: 32
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetCountries(params?: {}): Promise<implicitReturnType>;
    publicGetCurrencies(params?: {}): Promise<implicitReturnType>;
    publicGetDataCurrencyTicker(params?: {}): Promise<implicitReturnType>;
    publicGetDataCurrencyTrades(params?: {}): Promise<implicitReturnType>;
    publicGetDataCurrencyDepth(params?: {}): Promise<implicitReturnType>;
    publicGetBitcoinChartsIdTrades(params?: {}): Promise<implicitReturnType>;
    publicGetBitcoinChartsIdDepth(params?: {}): Promise<implicitReturnType>;
    privateGetUser(params?: {}): Promise<implicitReturnType>;
    privateGetUserAddresses(params?: {}): Promise<implicitReturnType>;
    privateGetUserAddressesAddress(params?: {}): Promise<implicitReturnType>;
    privateGetUserOrders(params?: {}): Promise<implicitReturnType>;
    privateGetUserOrdersUuid(params?: {}): Promise<implicitReturnType>;
    privateGetUserPriceAlerts(params?: {}): Promise<implicitReturnType>;
    privateGetMerchantGetPaymentUuid(params?: {}): Promise<implicitReturnType>;
    privatePostUserAddresses(params?: {}): Promise<implicitReturnType>;
    privatePostUserOrders(params?: {}): Promise<implicitReturnType>;
    privatePostUserWithdrawals(params?: {}): Promise<implicitReturnType>;
    privatePostUserEmailTransfers(params?: {}): Promise<implicitReturnType>;
    privatePostUserPaymentRequests(params?: {}): Promise<implicitReturnType>;
    privatePostUserPriceAlerts(params?: {}): Promise<implicitReturnType>;
    privatePostMerchantCreatePayment(params?: {}): Promise<implicitReturnType>;
    privateDeleteUserOrdersUuid(params?: {}): Promise<implicitReturnType>;
    privateDeleteUserOrdersUuidCancel(params?: {}): Promise<implicitReturnType>;
    privateDeleteUserPriceAlertsId(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/paymium.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 31
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
ts-node js/src/abstract/paymium.d.ts
```

