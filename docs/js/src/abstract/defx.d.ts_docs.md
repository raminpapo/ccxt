# Documentation: js/src/abstract/defx.d.ts

## File Metadata

- **Path**: `js/src/abstract/defx.d.ts`
- **Size**: 5,577 bytes
- **Lines**: 73
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    v1PublicGetHealthcheckPing(params?: {}): Promise<implicitReturnType>;
    v1PublicGetSymbolsSymbolOhlc(params?: {}): Promise<implicitReturnType>;
    v1PublicGetSymbolsSymbolTrades(params?: {}): Promise<implicitReturnType>;
    v1PublicGetSymbolsSymbolPrices(params?: {}): Promise<implicitReturnType>;
    v1PublicGetSymbolsSymbolTicker24hr(params?: {}): Promise<implicitReturnType>;
    v1PublicGetSymbolsSymbolDepthLevelSlab(params?: {}): Promise<implicitReturnType>;
    v1PublicGetTicker24HrAgg(params?: {}): Promise<implicitReturnType>;
    v1PublicGetCMarkets(params?: {}): Promise<implicitReturnType>;
    v1PublicGetCMarketsMetadata(params?: {}): Promise<implicitReturnType>;
    v1PublicGetAnalyticsMarketStatsNewUsers(params?: {}): Promise<implicitReturnType>;
    v1PublicGetAnalyticsMarketStatsTvl(params?: {}): Promise<implicitReturnType>;
    v1PublicGetAnalyticsMarketStatsVolumeByInstrument(params?: {}): Promise<implicitReturnType>;
    v1PublicGetAnalyticsMarketStatsLiquidation(params?: {}): Promise<implicitReturnType>;
    v1PublicGetAnalyticsMarketStatsTotalVolume(params?: {}): Promise<implicitReturnType>;
    v1PublicGetAnalyticsMarketStatsOpenInterest(params?: {}): Promise<implicitReturnType>;
    v1PublicGetAnalyticsMarketStatsTotalTrades(params?: {}): Promise<implicitReturnType>;
    v1PublicGetAnalyticsMarketStatsBasis(params?: {}): Promise<implicitReturnType>;
    v1PublicGetAnalyticsMarketStatsInsuranceFund(params?: {}): Promise<implicitReturnType>;
    v1PublicGetAnalyticsMarketStatsLongAndShortRatio(params?: {}): Promise<implicitReturnType>;
    v1PublicGetAnalyticsMarketStatsFundingRate(params?: {}): Promise<implicitReturnType>;
    v1PublicGetAnalyticsMarketOverview(params?: {}): Promise<implicitReturnType>;
    v1PublicGetExplorerSearch(params?: {}): Promise<implicitReturnType>;
    v1PublicGetExplorerTransactions(params?: {}): Promise<implicitReturnType>;
    v1PublicGetExplorerBlocks(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetApiOrderOrderId(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetApiOrders(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetApiOrdersOcoParentOrderId(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetApiTrades(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetApiPositionActive(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetApiUsersMetadataLeverage(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetApiUsersMetadataFeeMultiplier(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetApiUsersMetadataSlippage(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetApiUsersReferral(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetApiUsersApikeys(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetConnectionSignatureMessageEvm(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetApiUsersProfileWallets(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetApiNotifications(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetApiWalletBalance(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetApiWalletTransactions(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetApiAnalyticsUserOverview(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetApiAnalyticsUserPnl(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetApiAnalyticsPointsOverview(params?: {}): Promise<implicitReturnType>;
    v1PrivateGetApiAnalyticsPointsHistory(params?: {}): Promise<implicitReturnType>;
    v1PrivatePostApiOrder(params?: {}): Promise<implicitReturnType>;
    v1PrivatePostApiPositionOco(params?: {}): Promise<implicitReturnType>;
    v1PrivatePostApiUsersSocketListenKeys(params?: {}): Promise<implicitReturnType>;
    v1PrivatePostApiUsersMetadataLeverage(params?: {}): Promise<implicitReturnType>;
    v1PrivatePostApiUsersMetadataFeeMultiplier(params?: {}): Promise<implicitReturnType>;
    v1PrivatePostApiUsersMetadataSlippage(params?: {}): Promise<implicitReturnType>;
    v1PrivatePostApiUsersReferralRecordReferralSignup(params?: {}): Promise<implicitReturnType>;
    v1PrivatePostApiUsersApikeys(params?: {}): Promise<implicitReturnType>;
    v1PrivatePostApiUsersProfileWallets(params?: {}): Promise<implicitReturnType>;
    v1PrivatePostApiTransfersWithdrawal(params?: {}): Promise<implicitReturnType>;
    v1PrivatePostApiTransfersBridgeWithdrawal(params?: {}): Promise<implicitReturnType>;
    v1PrivatePutApiPositionUpdatePositionMargin(params?: {}): Promise<implicitReturnType>;
    v1PrivatePutApiUsersSocketListenKeysListenKey(params?: {}): Promise<implicitReturnType>;
    v1PrivatePutApiUsersApikeysAccessKeyStatus(params?: {}): Promise<implicitReturnType>;
    v1PrivatePutApiUsersReferral(params?: {}): Promise<implicitReturnType>;
    v1PrivatePatchApiUsersApikeysAccessKey(params?: {}): Promise<implicitReturnType>;
    v1PrivateDeleteApiOrdersAllOpen(params?: {}): Promise<implicitReturnType>;
    v1PrivateDeleteApiOrderOrderId(params?: {}): Promise<implicitReturnType>;
    v1PrivateDeleteApiPositionPositionId(params?: {}): Promise<implicitReturnType>;
    v1PrivateDeleteApiPositionAll(params?: {}): Promise<implicitReturnType>;
    v1PrivateDeleteApiUsersSocketListenKeysListenKey(params?: {}): Promise<implicitReturnType>;
    v1PrivateDeleteApiUsersApikeysAccessKey(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/defx.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 73
- Code lines: 72
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
ts-node js/src/abstract/defx.d.ts
```

