# Documentation: js/src/abstract/bitrue.d.ts

## File Metadata

- **Path**: `js/src/abstract/bitrue.d.ts`
- **Size**: 5,295 bytes
- **Lines**: 76
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    spotKlinePublicGetPublicJson(params?: {}): Promise<implicitReturnType>;
    spotKlinePublicGetPublicCurrencyJson(params?: {}): Promise<implicitReturnType>;
    spotV1PublicGetPing(params?: {}): Promise<implicitReturnType>;
    spotV1PublicGetTime(params?: {}): Promise<implicitReturnType>;
    spotV1PublicGetExchangeInfo(params?: {}): Promise<implicitReturnType>;
    spotV1PublicGetDepth(params?: {}): Promise<implicitReturnType>;
    spotV1PublicGetTrades(params?: {}): Promise<implicitReturnType>;
    spotV1PublicGetHistoricalTrades(params?: {}): Promise<implicitReturnType>;
    spotV1PublicGetAggTrades(params?: {}): Promise<implicitReturnType>;
    spotV1PublicGetTicker24hr(params?: {}): Promise<implicitReturnType>;
    spotV1PublicGetTickerPrice(params?: {}): Promise<implicitReturnType>;
    spotV1PublicGetTickerBookTicker(params?: {}): Promise<implicitReturnType>;
    spotV1PublicGetMarketKline(params?: {}): Promise<implicitReturnType>;
    spotV1PrivateGetOrder(params?: {}): Promise<implicitReturnType>;
    spotV1PrivateGetOpenOrders(params?: {}): Promise<implicitReturnType>;
    spotV1PrivateGetAllOrders(params?: {}): Promise<implicitReturnType>;
    spotV1PrivateGetAccount(params?: {}): Promise<implicitReturnType>;
    spotV1PrivateGetMyTrades(params?: {}): Promise<implicitReturnType>;
    spotV1PrivateGetEtfNetValueSymbol(params?: {}): Promise<implicitReturnType>;
    spotV1PrivateGetWithdrawHistory(params?: {}): Promise<implicitReturnType>;
    spotV1PrivateGetDepositHistory(params?: {}): Promise<implicitReturnType>;
    spotV1PrivatePostOrder(params?: {}): Promise<implicitReturnType>;
    spotV1PrivatePostWithdrawCommit(params?: {}): Promise<implicitReturnType>;
    spotV1PrivateDeleteOrder(params?: {}): Promise<implicitReturnType>;
    spotV2PrivateGetMyTrades(params?: {}): Promise<implicitReturnType>;
    fapiV1PublicGetPing(params?: {}): Promise<implicitReturnType>;
    fapiV1PublicGetTime(params?: {}): Promise<implicitReturnType>;
    fapiV1PublicGetContracts(params?: {}): Promise<implicitReturnType>;
    fapiV1PublicGetDepth(params?: {}): Promise<implicitReturnType>;
    fapiV1PublicGetTicker(params?: {}): Promise<implicitReturnType>;
    fapiV1PublicGetKlines(params?: {}): Promise<implicitReturnType>;
    fapiV2PrivateGetMyTrades(params?: {}): Promise<implicitReturnType>;
    fapiV2PrivateGetOpenOrders(params?: {}): Promise<implicitReturnType>;
    fapiV2PrivateGetOrder(params?: {}): Promise<implicitReturnType>;
    fapiV2PrivateGetAccount(params?: {}): Promise<implicitReturnType>;
    fapiV2PrivateGetLeverageBracket(params?: {}): Promise<implicitReturnType>;
    fapiV2PrivateGetCommissionRate(params?: {}): Promise<implicitReturnType>;
    fapiV2PrivateGetFuturesTransferHistory(params?: {}): Promise<implicitReturnType>;
    fapiV2PrivateGetForceOrdersHistory(params?: {}): Promise<implicitReturnType>;
    fapiV2PrivatePostPositionMargin(params?: {}): Promise<implicitReturnType>;
    fapiV2PrivatePostLevelEdit(params?: {}): Promise<implicitReturnType>;
    fapiV2PrivatePostCancel(params?: {}): Promise<implicitReturnType>;
    fapiV2PrivatePostOrder(params?: {}): Promise<implicitReturnType>;
    fapiV2PrivatePostAllOpenOrders(params?: {}): Promise<implicitReturnType>;
    fapiV2PrivatePostFuturesTransfer(params?: {}): Promise<implicitReturnType>;
    dapiV1PublicGetPing(params?: {}): Promise<implicitReturnType>;
    dapiV1PublicGetTime(params?: {}): Promise<implicitReturnType>;
    dapiV1PublicGetContracts(params?: {}): Promise<implicitReturnType>;
    dapiV1PublicGetDepth(params?: {}): Promise<implicitReturnType>;
    dapiV1PublicGetTicker(params?: {}): Promise<implicitReturnType>;
    dapiV1PublicGetKlines(params?: {}): Promise<implicitReturnType>;
    dapiV2PrivateGetMyTrades(params?: {}): Promise<implicitReturnType>;
    dapiV2PrivateGetOpenOrders(params?: {}): Promise<implicitReturnType>;
    dapiV2PrivateGetOrder(params?: {}): Promise<implicitReturnType>;
    dapiV2PrivateGetAccount(params?: {}): Promise<implicitReturnType>;
    dapiV2PrivateGetLeverageBracket(params?: {}): Promise<implicitReturnType>;
    dapiV2PrivateGetCommissionRate(params?: {}): Promise<implicitReturnType>;
    dapiV2PrivateGetFuturesTransferHistory(params?: {}): Promise<implicitReturnType>;
    dapiV2PrivateGetForceOrdersHistory(params?: {}): Promise<implicitReturnType>;
    dapiV2PrivatePostPositionMargin(params?: {}): Promise<implicitReturnType>;
    dapiV2PrivatePostLevelEdit(params?: {}): Promise<implicitReturnType>;
    dapiV2PrivatePostCancel(params?: {}): Promise<implicitReturnType>;
    dapiV2PrivatePostOrder(params?: {}): Promise<implicitReturnType>;
    dapiV2PrivatePostAllOpenOrders(params?: {}): Promise<implicitReturnType>;
    dapiV2PrivatePostFuturesTransfer(params?: {}): Promise<implicitReturnType>;
    openV1PrivatePostPoseidonApiV1ListenKey(params?: {}): Promise<implicitReturnType>;
    openV1PrivatePutPoseidonApiV1ListenKeyListenKey(params?: {}): Promise<implicitReturnType>;
    openV1PrivateDeletePoseidonApiV1ListenKeyListenKey(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/bitrue.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 76
- Code lines: 75
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
ts-node js/src/abstract/bitrue.d.ts
```

