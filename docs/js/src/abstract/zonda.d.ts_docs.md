# Documentation: js/src/abstract/zonda.d.ts

## File Metadata

- **Path**: `js/src/abstract/zonda.d.ts`
- **Size**: 4,292 bytes
- **Lines**: 57
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetIdAll(params?: {}): Promise<implicitReturnType>;
    publicGetIdMarket(params?: {}): Promise<implicitReturnType>;
    publicGetIdOrderbook(params?: {}): Promise<implicitReturnType>;
    publicGetIdTicker(params?: {}): Promise<implicitReturnType>;
    publicGetIdTrades(params?: {}): Promise<implicitReturnType>;
    privatePostInfo(params?: {}): Promise<implicitReturnType>;
    privatePostTrade(params?: {}): Promise<implicitReturnType>;
    privatePostCancel(params?: {}): Promise<implicitReturnType>;
    privatePostOrderbook(params?: {}): Promise<implicitReturnType>;
    privatePostOrders(params?: {}): Promise<implicitReturnType>;
    privatePostTransfer(params?: {}): Promise<implicitReturnType>;
    privatePostWithdraw(params?: {}): Promise<implicitReturnType>;
    privatePostHistory(params?: {}): Promise<implicitReturnType>;
    privatePostTransactions(params?: {}): Promise<implicitReturnType>;
    v1_01PublicGetTradingTicker(params?: {}): Promise<implicitReturnType>;
    v1_01PublicGetTradingTickerSymbol(params?: {}): Promise<implicitReturnType>;
    v1_01PublicGetTradingStats(params?: {}): Promise<implicitReturnType>;
    v1_01PublicGetTradingStatsSymbol(params?: {}): Promise<implicitReturnType>;
    v1_01PublicGetTradingOrderbookSymbol(params?: {}): Promise<implicitReturnType>;
    v1_01PublicGetTradingTransactionsSymbol(params?: {}): Promise<implicitReturnType>;
    v1_01PublicGetTradingCandleHistorySymbolResolution(params?: {}): Promise<implicitReturnType>;
    v1_01PrivateGetApiPaymentsDepositsCryptoAddresses(params?: {}): Promise<implicitReturnType>;
    v1_01PrivateGetPaymentsWithdrawalDetailId(params?: {}): Promise<implicitReturnType>;
    v1_01PrivateGetPaymentsDepositDetailId(params?: {}): Promise<implicitReturnType>;
    v1_01PrivateGetTradingOffer(params?: {}): Promise<implicitReturnType>;
    v1_01PrivateGetTradingStopOffer(params?: {}): Promise<implicitReturnType>;
    v1_01PrivateGetTradingConfigSymbol(params?: {}): Promise<implicitReturnType>;
    v1_01PrivateGetTradingHistoryTransactions(params?: {}): Promise<implicitReturnType>;
    v1_01PrivateGetBalancesBITBAYHistory(params?: {}): Promise<implicitReturnType>;
    v1_01PrivateGetBalancesBITBAYBalance(params?: {}): Promise<implicitReturnType>;
    v1_01PrivateGetFiatCantorRateBaseIdQuoteId(params?: {}): Promise<implicitReturnType>;
    v1_01PrivateGetFiatCantorHistory(params?: {}): Promise<implicitReturnType>;
    v1_01PrivateGetClientPaymentsV2CustomerCryptoCurrencyChannelsDeposit(params?: {}): Promise<implicitReturnType>;
    v1_01PrivateGetClientPaymentsV2CustomerCryptoCurrencyChannelsWithdrawal(params?: {}): Promise<implicitReturnType>;
    v1_01PrivateGetClientPaymentsV2CustomerCryptoDepositFee(params?: {}): Promise<implicitReturnType>;
    v1_01PrivateGetClientPaymentsV2CustomerCryptoWithdrawalFee(params?: {}): Promise<implicitReturnType>;
    v1_01PrivatePostTradingOfferSymbol(params?: {}): Promise<implicitReturnType>;
    v1_01PrivatePostTradingStopOfferSymbol(params?: {}): Promise<implicitReturnType>;
    v1_01PrivatePostTradingConfigSymbol(params?: {}): Promise<implicitReturnType>;
    v1_01PrivatePostBalancesBITBAYBalance(params?: {}): Promise<implicitReturnType>;
    v1_01PrivatePostBalancesBITBAYBalanceTransferSourceDestination(params?: {}): Promise<implicitReturnType>;
    v1_01PrivatePostFiatCantorExchange(params?: {}): Promise<implicitReturnType>;
    v1_01PrivatePostApiPaymentsWithdrawalsCrypto(params?: {}): Promise<implicitReturnType>;
    v1_01PrivatePostApiPaymentsWithdrawalsFiat(params?: {}): Promise<implicitReturnType>;
    v1_01PrivatePostClientPaymentsV2CustomerCryptoDeposit(params?: {}): Promise<implicitReturnType>;
    v1_01PrivatePostClientPaymentsV2CustomerCryptoWithdrawal(params?: {}): Promise<implicitReturnType>;
    v1_01PrivateDeleteTradingOfferSymbolIdSidePrice(params?: {}): Promise<implicitReturnType>;
    v1_01PrivateDeleteTradingStopOfferSymbolIdSidePrice(params?: {}): Promise<implicitReturnType>;
    v1_01PrivatePutBalancesBITBAYBalanceId(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/zonda.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 57
- Code lines: 56
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
ts-node js/src/abstract/zonda.d.ts
```

