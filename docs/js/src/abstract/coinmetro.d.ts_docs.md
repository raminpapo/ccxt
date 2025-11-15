# Documentation: js/src/abstract/coinmetro.d.ts

## File Metadata

- **Path**: `js/src/abstract/coinmetro.d.ts`
- **Size**: 2,483 bytes
- **Lines**: 38
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetDemoTemp(params?: {}): Promise<implicitReturnType>;
    publicGetExchangeCandlesPairTimeframeFromTo(params?: {}): Promise<implicitReturnType>;
    publicGetExchangePrices(params?: {}): Promise<implicitReturnType>;
    publicGetExchangeTicksPairFrom(params?: {}): Promise<implicitReturnType>;
    publicGetAssets(params?: {}): Promise<implicitReturnType>;
    publicGetMarkets(params?: {}): Promise<implicitReturnType>;
    publicGetExchangeBookPair(params?: {}): Promise<implicitReturnType>;
    publicGetExchangeBookUpdatesPairFrom(params?: {}): Promise<implicitReturnType>;
    privateGetUsersBalances(params?: {}): Promise<implicitReturnType>;
    privateGetUsersWallets(params?: {}): Promise<implicitReturnType>;
    privateGetUsersWalletsHistorySince(params?: {}): Promise<implicitReturnType>;
    privateGetExchangeOrdersStatusOrderID(params?: {}): Promise<implicitReturnType>;
    privateGetExchangeOrdersActive(params?: {}): Promise<implicitReturnType>;
    privateGetExchangeOrdersHistorySince(params?: {}): Promise<implicitReturnType>;
    privateGetExchangeFillsSince(params?: {}): Promise<implicitReturnType>;
    privateGetExchangeMargin(params?: {}): Promise<implicitReturnType>;
    privatePostJwt(params?: {}): Promise<implicitReturnType>;
    privatePostJwtDevice(params?: {}): Promise<implicitReturnType>;
    privatePostDevices(params?: {}): Promise<implicitReturnType>;
    privatePostJwtReadOnly(params?: {}): Promise<implicitReturnType>;
    privatePostExchangeOrdersCreate(params?: {}): Promise<implicitReturnType>;
    privatePostExchangeOrdersModifyOrderID(params?: {}): Promise<implicitReturnType>;
    privatePostExchangeSwap(params?: {}): Promise<implicitReturnType>;
    privatePostExchangeSwapConfirmSwapId(params?: {}): Promise<implicitReturnType>;
    privatePostExchangeOrdersCloseOrderID(params?: {}): Promise<implicitReturnType>;
    privatePostExchangeOrdersHedge(params?: {}): Promise<implicitReturnType>;
    privatePutJwt(params?: {}): Promise<implicitReturnType>;
    privatePutExchangeOrdersCancelOrderID(params?: {}): Promise<implicitReturnType>;
    privatePutUsersMarginCollateral(params?: {}): Promise<implicitReturnType>;
    privatePutUsersMarginPrimaryCurrency(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/coinmetro.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 38
- Code lines: 37
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
ts-node js/src/abstract/coinmetro.d.ts
```

