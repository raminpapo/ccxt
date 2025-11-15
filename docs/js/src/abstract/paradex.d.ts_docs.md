# Documentation: js/src/abstract/paradex.d.ts

## File Metadata

- **Path**: `js/src/abstract/paradex.d.ts`
- **Size**: 4,402 bytes
- **Lines**: 67
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetBboMarket(params?: {}): Promise<implicitReturnType>;
    publicGetFundingData(params?: {}): Promise<implicitReturnType>;
    publicGetMarkets(params?: {}): Promise<implicitReturnType>;
    publicGetMarketsKlines(params?: {}): Promise<implicitReturnType>;
    publicGetMarketsSummary(params?: {}): Promise<implicitReturnType>;
    publicGetOrderbookMarket(params?: {}): Promise<implicitReturnType>;
    publicGetInsurance(params?: {}): Promise<implicitReturnType>;
    publicGetReferralsConfig(params?: {}): Promise<implicitReturnType>;
    publicGetSystemConfig(params?: {}): Promise<implicitReturnType>;
    publicGetSystemState(params?: {}): Promise<implicitReturnType>;
    publicGetSystemTime(params?: {}): Promise<implicitReturnType>;
    publicGetTrades(params?: {}): Promise<implicitReturnType>;
    publicGetVaults(params?: {}): Promise<implicitReturnType>;
    publicGetVaultsBalance(params?: {}): Promise<implicitReturnType>;
    publicGetVaultsConfig(params?: {}): Promise<implicitReturnType>;
    publicGetVaultsHistory(params?: {}): Promise<implicitReturnType>;
    publicGetVaultsPositions(params?: {}): Promise<implicitReturnType>;
    publicGetVaultsSummary(params?: {}): Promise<implicitReturnType>;
    publicGetVaultsTransfers(params?: {}): Promise<implicitReturnType>;
    privateGetAccount(params?: {}): Promise<implicitReturnType>;
    privateGetAccountInfo(params?: {}): Promise<implicitReturnType>;
    privateGetAccountHistory(params?: {}): Promise<implicitReturnType>;
    privateGetAccountMargin(params?: {}): Promise<implicitReturnType>;
    privateGetAccountProfile(params?: {}): Promise<implicitReturnType>;
    privateGetAccountSubaccounts(params?: {}): Promise<implicitReturnType>;
    privateGetBalance(params?: {}): Promise<implicitReturnType>;
    privateGetFills(params?: {}): Promise<implicitReturnType>;
    privateGetFundingPayments(params?: {}): Promise<implicitReturnType>;
    privateGetPositions(params?: {}): Promise<implicitReturnType>;
    privateGetTradebusts(params?: {}): Promise<implicitReturnType>;
    privateGetTransactions(params?: {}): Promise<implicitReturnType>;
    privateGetLiquidations(params?: {}): Promise<implicitReturnType>;
    privateGetOrders(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersHistory(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersByClientIdClientId(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersOrderId(params?: {}): Promise<implicitReturnType>;
    privateGetPointsDataMarketProgram(params?: {}): Promise<implicitReturnType>;
    privateGetReferralsQrCode(params?: {}): Promise<implicitReturnType>;
    privateGetReferralsSummary(params?: {}): Promise<implicitReturnType>;
    privateGetTransfers(params?: {}): Promise<implicitReturnType>;
    privateGetAlgoOrders(params?: {}): Promise<implicitReturnType>;
    privateGetAlgoOrdersHistory(params?: {}): Promise<implicitReturnType>;
    privateGetAlgoOrdersAlgoId(params?: {}): Promise<implicitReturnType>;
    privateGetVaultsAccountSummary(params?: {}): Promise<implicitReturnType>;
    privatePostAccountMarginMarket(params?: {}): Promise<implicitReturnType>;
    privatePostAccountProfileMaxSlippage(params?: {}): Promise<implicitReturnType>;
    privatePostAccountProfileReferralCode(params?: {}): Promise<implicitReturnType>;
    privatePostAccountProfileUsername(params?: {}): Promise<implicitReturnType>;
    privatePostAuth(params?: {}): Promise<implicitReturnType>;
    privatePostOnboarding(params?: {}): Promise<implicitReturnType>;
    privatePostOrders(params?: {}): Promise<implicitReturnType>;
    privatePostOrdersBatch(params?: {}): Promise<implicitReturnType>;
    privatePostAlgoOrders(params?: {}): Promise<implicitReturnType>;
    privatePostVaults(params?: {}): Promise<implicitReturnType>;
    privatePutOrdersOrderId(params?: {}): Promise<implicitReturnType>;
    privateDeleteOrders(params?: {}): Promise<implicitReturnType>;
    privateDeleteOrdersByClientIdClientId(params?: {}): Promise<implicitReturnType>;
    privateDeleteOrdersOrderId(params?: {}): Promise<implicitReturnType>;
    privateDeleteAlgoOrdersAlgoId(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/paradex.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 67
- Code lines: 66
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
ts-node js/src/abstract/paradex.d.ts
```

