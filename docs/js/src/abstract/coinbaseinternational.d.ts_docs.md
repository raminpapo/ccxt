# Documentation: js/src/abstract/coinbaseinternational.d.ts

## File Metadata

- **Path**: `js/src/abstract/coinbaseinternational.d.ts`
- **Size**: 2,977 bytes
- **Lines**: 43
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    v1PublicGetAssets(params?: {}): Promise<implicitReturnType>;
    v1PublicGetAssetsAssets(params?: {}): Promise<implicitReturnType>;
    v1PublicGetAssetsAssetNetworks(params?: {}): Promise<implicitReturnType>;
    v1PublicGetInstruments(params?: {}): Promise<implicitReturnType>;
    v1PublicGetInstrumentsInstrument(params?: {}): Promise<implicitReturnType>;
    v1PublicGetInstrumentsInstrumentQuote(params?: {}): Promise<implicitReturnType>;
    v1PublicGetInstrumentsInstrumentFunding(params?: {}): Promise<implicitReturnType>;
    v1PublicGetInstrumentsInstrumentCandles(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetOrders(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetOrdersId(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetPortfolios(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetPortfoliosPortfolio(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetPortfoliosPortfolioDetail(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetPortfoliosPortfolioSummary(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetPortfoliosPortfolioBalances(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetPortfoliosPortfolioBalancesAsset(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetPortfoliosPortfolioPositions(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetPortfoliosPortfolioPositionsInstrument(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetPortfoliosFills(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetPortfoliosPortfolioFills(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetTransfers(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetTransfersTransferUuid(params?: {}): Promise<implicitReturnType>;
    v1PrivatePostOrders(params?: {}): Promise<implicitReturnType>;
    v1PrivatePostPortfolios(params?: {}): Promise<implicitReturnType>;
    v1PrivatePostPortfoliosMargin(params?: {}): Promise<implicitReturnType>;
    v1PrivatePostPortfoliosTransfer(params?: {}): Promise<implicitReturnType>;
    v1PrivatePostTransfersWithdraw(params?: {}): Promise<implicitReturnType>;
    v1PrivatePostTransfersAddress(params?: {}): Promise<implicitReturnType>;
    v1PrivatePostTransfersCreateCounterpartyId(params?: {}): Promise<implicitReturnType>;
    v1PrivatePostTransfersValidateCounterpartyId(params?: {}): Promise<implicitReturnType>;
    v1PrivatePostTransfersWithdrawCounterparty(params?: {}): Promise<implicitReturnType>;
    v1PrivatePutOrdersId(params?: {}): Promise<implicitReturnType>;
    v1PrivatePutPortfoliosPortfolio(params?: {}): Promise<implicitReturnType>;
    v1PrivateDeleteOrders(params?: {}): Promise<implicitReturnType>;
    v1PrivateDeleteOrdersId(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/coinbaseinternational.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 43
- Code lines: 42
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
ts-node js/src/abstract/coinbaseinternational.d.ts
```

