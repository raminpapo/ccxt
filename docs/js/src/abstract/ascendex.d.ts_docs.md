# Documentation: js/src/abstract/ascendex.d.ts

## File Metadata

- **Path**: `js/src/abstract/ascendex.d.ts`
- **Size**: 6,152 bytes
- **Lines**: 81
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    v1PublicGetAssets(params?: {}): Promise<implicitReturnType>;
    v1PublicGetProducts(params?: {}): Promise<implicitReturnType>;
    v1PublicGetTicker(params?: {}): Promise<implicitReturnType>;
    v1PublicGetBarhistInfo(params?: {}): Promise<implicitReturnType>;
    v1PublicGetBarhist(params?: {}): Promise<implicitReturnType>;
    v1PublicGetDepth(params?: {}): Promise<implicitReturnType>;
    v1PublicGetTrades(params?: {}): Promise<implicitReturnType>;
    v1PublicGetCashAssets(params?: {}): Promise<implicitReturnType>;
    v1PublicGetCashProducts(params?: {}): Promise<implicitReturnType>;
    v1PublicGetMarginAssets(params?: {}): Promise<implicitReturnType>;
    v1PublicGetMarginProducts(params?: {}): Promise<implicitReturnType>;
    v1PublicGetFuturesCollateral(params?: {}): Promise<implicitReturnType>;
    v1PublicGetFuturesContracts(params?: {}): Promise<implicitReturnType>;
    v1PublicGetFuturesRefPx(params?: {}): Promise<implicitReturnType>;
    v1PublicGetFuturesMarketData(params?: {}): Promise<implicitReturnType>;
    v1PublicGetFuturesFundingRates(params?: {}): Promise<implicitReturnType>;
    v1PublicGetRiskLimitInfo(params?: {}): Promise<implicitReturnType>;
    v1PublicGetExchangeInfo(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetInfo(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetWalletTransactions(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetWalletDepositAddress(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetDataBalanceSnapshot(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetDataBalanceHistory(params?: {}): Promise<implicitReturnType>;
    v1PrivateAccountCategoryGetBalance(params?: {}): Promise<implicitReturnType>;
    v1PrivateAccountCategoryGetOrderOpen(params?: {}): Promise<implicitReturnType>;
    v1PrivateAccountCategoryGetOrderStatus(params?: {}): Promise<implicitReturnType>;
    v1PrivateAccountCategoryGetOrderHistCurrent(params?: {}): Promise<implicitReturnType>;
    v1PrivateAccountCategoryGetRisk(params?: {}): Promise<implicitReturnType>;
    v1PrivateAccountCategoryPostOrder(params?: {}): Promise<implicitReturnType>;
    v1PrivateAccountCategoryPostOrderBatch(params?: {}): Promise<implicitReturnType>;
    v1PrivateAccountCategoryDeleteOrder(params?: {}): Promise<implicitReturnType>;
    v1PrivateAccountCategoryDeleteOrderAll(params?: {}): Promise<implicitReturnType>;
    v1PrivateAccountCategoryDeleteOrderBatch(params?: {}): Promise<implicitReturnType>;
    v1PrivateAccountGroupGetCashBalance(params?: {}): Promise<implicitReturnType>;
    v1PrivateAccountGroupGetMarginBalance(params?: {}): Promise<implicitReturnType>;
    v1PrivateAccountGroupGetMarginRisk(params?: {}): Promise<implicitReturnType>;
    v1PrivateAccountGroupGetFuturesCollateralBalance(params?: {}): Promise<implicitReturnType>;
    v1PrivateAccountGroupGetFuturesPosition(params?: {}): Promise<implicitReturnType>;
    v1PrivateAccountGroupGetFuturesRisk(params?: {}): Promise<implicitReturnType>;
    v1PrivateAccountGroupGetFuturesFundingPayments(params?: {}): Promise<implicitReturnType>;
    v1PrivateAccountGroupGetOrderHist(params?: {}): Promise<implicitReturnType>;
    v1PrivateAccountGroupGetSpotFee(params?: {}): Promise<implicitReturnType>;
    v1PrivateAccountGroupPostTransfer(params?: {}): Promise<implicitReturnType>;
    v1PrivateAccountGroupPostFuturesTransferDeposit(params?: {}): Promise<implicitReturnType>;
    v1PrivateAccountGroupPostFuturesTransferWithdraw(params?: {}): Promise<implicitReturnType>;
    v2PublicGetAssets(params?: {}): Promise<implicitReturnType>;
    v2PublicGetFuturesContract(params?: {}): Promise<implicitReturnType>;
    v2PublicGetFuturesCollateral(params?: {}): Promise<implicitReturnType>;
    v2PublicGetFuturesPricingData(params?: {}): Promise<implicitReturnType>;
    v2PublicGetFuturesTicker(params?: {}): Promise<implicitReturnType>;
    v2PublicGetRiskLimitInfo(params?: {}): Promise<implicitReturnType>;
    v2PrivateDataGetOrderHist(params?: {}): Promise<implicitReturnType>;
    v2PrivateGetAccountInfo(params?: {}): Promise<implicitReturnType>;
    v2PrivateAccountGroupGetOrderHist(params?: {}): Promise<implicitReturnType>;
    v2PrivateAccountGroupGetFuturesPosition(params?: {}): Promise<implicitReturnType>;
    v2PrivateAccountGroupGetFuturesFreeMargin(params?: {}): Promise<implicitReturnType>;
    v2PrivateAccountGroupGetFuturesOrderHistCurrent(params?: {}): Promise<implicitReturnType>;
    v2PrivateAccountGroupGetFuturesFundingPayments(params?: {}): Promise<implicitReturnType>;
    v2PrivateAccountGroupGetFuturesOrderOpen(params?: {}): Promise<implicitReturnType>;
    v2PrivateAccountGroupGetFuturesOrderStatus(params?: {}): Promise<implicitReturnType>;
    v2PrivateAccountGroupPostFuturesIsolatedPositionMargin(params?: {}): Promise<implicitReturnType>;
    v2PrivateAccountGroupPostFuturesMarginType(params?: {}): Promise<implicitReturnType>;
    v2PrivateAccountGroupPostFuturesLeverage(params?: {}): Promise<implicitReturnType>;
    v2PrivateAccountGroupPostFuturesTransferDeposit(params?: {}): Promise<implicitReturnType>;
    v2PrivateAccountGroupPostFuturesTransferWithdraw(params?: {}): Promise<implicitReturnType>;
    v2PrivateAccountGroupPostFuturesOrder(params?: {}): Promise<implicitReturnType>;
    v2PrivateAccountGroupPostFuturesOrderBatch(params?: {}): Promise<implicitReturnType>;
    v2PrivateAccountGroupPostFuturesOrderOpen(params?: {}): Promise<implicitReturnType>;
    v2PrivateAccountGroupPostSubuserSubuserTransfer(params?: {}): Promise<implicitReturnType>;
    v2PrivateAccountGroupPostSubuserSubuserTransferHist(params?: {}): Promise<implicitReturnType>;
    v2PrivateAccountGroupDeleteFuturesOrder(params?: {}): Promise<implicitReturnType>;
    v2PrivateAccountGroupDeleteFuturesOrderBatch(params?: {}): Promise<implicitReturnType>;
    v2PrivateAccountGroupDeleteFuturesOrderAll(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/ascendex.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 81
- Code lines: 80
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
ts-node js/src/abstract/ascendex.d.ts
```

