# Documentation: js/src/abstract/bigone.d.ts

## File Metadata

- **Path**: `js/src/abstract/bigone.d.ts`
- **Size**: 3,290 bytes
- **Lines**: 49
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetPing(params?: {}): Promise<implicitReturnType>;
    publicGetAssetPairs(params?: {}): Promise<implicitReturnType>;
    publicGetAssetPairsAssetPairNameDepth(params?: {}): Promise<implicitReturnType>;
    publicGetAssetPairsAssetPairNameTrades(params?: {}): Promise<implicitReturnType>;
    publicGetAssetPairsAssetPairNameTicker(params?: {}): Promise<implicitReturnType>;
    publicGetAssetPairsAssetPairNameCandles(params?: {}): Promise<implicitReturnType>;
    publicGetAssetPairsTickers(params?: {}): Promise<implicitReturnType>;
    privateGetAccounts(params?: {}): Promise<implicitReturnType>;
    privateGetFundAccounts(params?: {}): Promise<implicitReturnType>;
    privateGetAssetsAssetSymbolAddress(params?: {}): Promise<implicitReturnType>;
    privateGetOrders(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersId(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersMulti(params?: {}): Promise<implicitReturnType>;
    privateGetTrades(params?: {}): Promise<implicitReturnType>;
    privateGetWithdrawals(params?: {}): Promise<implicitReturnType>;
    privateGetDeposits(params?: {}): Promise<implicitReturnType>;
    privatePostOrders(params?: {}): Promise<implicitReturnType>;
    privatePostOrdersIdCancel(params?: {}): Promise<implicitReturnType>;
    privatePostOrdersCancel(params?: {}): Promise<implicitReturnType>;
    privatePostWithdrawals(params?: {}): Promise<implicitReturnType>;
    privatePostTransfer(params?: {}): Promise<implicitReturnType>;
    contractPublicGetSymbols(params?: {}): Promise<implicitReturnType>;
    contractPublicGetInstruments(params?: {}): Promise<implicitReturnType>;
    contractPublicGetDepthSymbolSnapshot(params?: {}): Promise<implicitReturnType>;
    contractPublicGetInstrumentsDifference(params?: {}): Promise<implicitReturnType>;
    contractPublicGetInstrumentsPrices(params?: {}): Promise<implicitReturnType>;
    contractPrivateGetAccounts(params?: {}): Promise<implicitReturnType>;
    contractPrivateGetOrdersId(params?: {}): Promise<implicitReturnType>;
    contractPrivateGetOrders(params?: {}): Promise<implicitReturnType>;
    contractPrivateGetOrdersOpening(params?: {}): Promise<implicitReturnType>;
    contractPrivateGetOrdersCount(params?: {}): Promise<implicitReturnType>;
    contractPrivateGetOrdersOpeningCount(params?: {}): Promise<implicitReturnType>;
    contractPrivateGetTrades(params?: {}): Promise<implicitReturnType>;
    contractPrivateGetTradesCount(params?: {}): Promise<implicitReturnType>;
    contractPrivatePostOrders(params?: {}): Promise<implicitReturnType>;
    contractPrivatePostOrdersBatch(params?: {}): Promise<implicitReturnType>;
    contractPrivatePutPositionsSymbolMargin(params?: {}): Promise<implicitReturnType>;
    contractPrivatePutPositionsSymbolRiskLimit(params?: {}): Promise<implicitReturnType>;
    contractPrivateDeleteOrdersId(params?: {}): Promise<implicitReturnType>;
    contractPrivateDeleteOrdersBatch(params?: {}): Promise<implicitReturnType>;
    webExchangeGetV3Assets(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/bigone.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 49
- Code lines: 48
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
ts-node js/src/abstract/bigone.d.ts
```

