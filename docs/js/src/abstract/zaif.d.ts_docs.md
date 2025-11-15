# Documentation: js/src/abstract/zaif.d.ts

## File Metadata

- **Path**: `js/src/abstract/zaif.d.ts`
- **Size**: 2,615 bytes
- **Lines**: 42
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetDepthPair(params?: {}): Promise<implicitReturnType>;
    publicGetCurrenciesPair(params?: {}): Promise<implicitReturnType>;
    publicGetCurrenciesAll(params?: {}): Promise<implicitReturnType>;
    publicGetCurrencyPairsPair(params?: {}): Promise<implicitReturnType>;
    publicGetCurrencyPairsAll(params?: {}): Promise<implicitReturnType>;
    publicGetLastPricePair(params?: {}): Promise<implicitReturnType>;
    publicGetTickerPair(params?: {}): Promise<implicitReturnType>;
    publicGetTradesPair(params?: {}): Promise<implicitReturnType>;
    privatePostActiveOrders(params?: {}): Promise<implicitReturnType>;
    privatePostCancelOrder(params?: {}): Promise<implicitReturnType>;
    privatePostDepositHistory(params?: {}): Promise<implicitReturnType>;
    privatePostGetIdInfo(params?: {}): Promise<implicitReturnType>;
    privatePostGetInfo(params?: {}): Promise<implicitReturnType>;
    privatePostGetInfo2(params?: {}): Promise<implicitReturnType>;
    privatePostGetPersonalInfo(params?: {}): Promise<implicitReturnType>;
    privatePostTrade(params?: {}): Promise<implicitReturnType>;
    privatePostTradeHistory(params?: {}): Promise<implicitReturnType>;
    privatePostWithdraw(params?: {}): Promise<implicitReturnType>;
    privatePostWithdrawHistory(params?: {}): Promise<implicitReturnType>;
    ecapiPostCreateInvoice(params?: {}): Promise<implicitReturnType>;
    ecapiPostGetInvoice(params?: {}): Promise<implicitReturnType>;
    ecapiPostGetInvoiceIdsByOrderNumber(params?: {}): Promise<implicitReturnType>;
    ecapiPostCancelInvoice(params?: {}): Promise<implicitReturnType>;
    tlapiPostGetPositions(params?: {}): Promise<implicitReturnType>;
    tlapiPostPositionHistory(params?: {}): Promise<implicitReturnType>;
    tlapiPostActivePositions(params?: {}): Promise<implicitReturnType>;
    tlapiPostCreatePosition(params?: {}): Promise<implicitReturnType>;
    tlapiPostChangePosition(params?: {}): Promise<implicitReturnType>;
    tlapiPostCancelPosition(params?: {}): Promise<implicitReturnType>;
    fapiGetGroupsGroupId(params?: {}): Promise<implicitReturnType>;
    fapiGetLastPriceGroupIdPair(params?: {}): Promise<implicitReturnType>;
    fapiGetTickerGroupIdPair(params?: {}): Promise<implicitReturnType>;
    fapiGetTradesGroupIdPair(params?: {}): Promise<implicitReturnType>;
    fapiGetDepthGroupIdPair(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/zaif.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 42
- Code lines: 41
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
ts-node js/src/abstract/zaif.d.ts
```

