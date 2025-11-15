# Documentation: js/src/abstract/upbit.d.ts

## File Metadata

- **Path**: `js/src/abstract/upbit.d.ts`
- **Size**: 3,932 bytes
- **Lines**: 60
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetMarketAll(params?: {}): Promise<implicitReturnType>;
    publicGetCandlesTimeframe(params?: {}): Promise<implicitReturnType>;
    publicGetCandlesTimeframeUnit(params?: {}): Promise<implicitReturnType>;
    publicGetCandlesSeconds(params?: {}): Promise<implicitReturnType>;
    publicGetCandlesMinutesUnit(params?: {}): Promise<implicitReturnType>;
    publicGetCandlesMinutes1(params?: {}): Promise<implicitReturnType>;
    publicGetCandlesMinutes3(params?: {}): Promise<implicitReturnType>;
    publicGetCandlesMinutes5(params?: {}): Promise<implicitReturnType>;
    publicGetCandlesMinutes10(params?: {}): Promise<implicitReturnType>;
    publicGetCandlesMinutes15(params?: {}): Promise<implicitReturnType>;
    publicGetCandlesMinutes30(params?: {}): Promise<implicitReturnType>;
    publicGetCandlesMinutes60(params?: {}): Promise<implicitReturnType>;
    publicGetCandlesMinutes240(params?: {}): Promise<implicitReturnType>;
    publicGetCandlesDays(params?: {}): Promise<implicitReturnType>;
    publicGetCandlesWeeks(params?: {}): Promise<implicitReturnType>;
    publicGetCandlesMonths(params?: {}): Promise<implicitReturnType>;
    publicGetCandlesYears(params?: {}): Promise<implicitReturnType>;
    publicGetTradesTicks(params?: {}): Promise<implicitReturnType>;
    publicGetTicker(params?: {}): Promise<implicitReturnType>;
    publicGetTickerAll(params?: {}): Promise<implicitReturnType>;
    publicGetOrderbook(params?: {}): Promise<implicitReturnType>;
    publicGetOrderbookInstruments(params?: {}): Promise<implicitReturnType>;
    publicGetOrderbookSupportedLevels(params?: {}): Promise<implicitReturnType>;
    privateGetAccounts(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersChance(params?: {}): Promise<implicitReturnType>;
    privateGetOrder(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersClosed(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersOpen(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersUuids(params?: {}): Promise<implicitReturnType>;
    privateGetWithdraws(params?: {}): Promise<implicitReturnType>;
    privateGetWithdraw(params?: {}): Promise<implicitReturnType>;
    privateGetWithdrawsChance(params?: {}): Promise<implicitReturnType>;
    privateGetWithdrawsCoinAddresses(params?: {}): Promise<implicitReturnType>;
    privateGetDeposits(params?: {}): Promise<implicitReturnType>;
    privateGetDepositsChanceCoin(params?: {}): Promise<implicitReturnType>;
    privateGetDeposit(params?: {}): Promise<implicitReturnType>;
    privateGetDepositsCoinAddresses(params?: {}): Promise<implicitReturnType>;
    privateGetDepositsCoinAddress(params?: {}): Promise<implicitReturnType>;
    privateGetTravelRuleVasps(params?: {}): Promise<implicitReturnType>;
    privateGetStatusWallet(params?: {}): Promise<implicitReturnType>;
    privateGetApiKeys(params?: {}): Promise<implicitReturnType>;
    privatePostOrders(params?: {}): Promise<implicitReturnType>;
    privatePostOrdersCancelAndNew(params?: {}): Promise<implicitReturnType>;
    privatePostWithdrawsCoin(params?: {}): Promise<implicitReturnType>;
    privatePostWithdrawsKrw(params?: {}): Promise<implicitReturnType>;
    privatePostDepositsKrw(params?: {}): Promise<implicitReturnType>;
    privatePostDepositsGenerateCoinAddress(params?: {}): Promise<implicitReturnType>;
    privatePostTravelRuleDepositUuid(params?: {}): Promise<implicitReturnType>;
    privatePostTravelRuleDepositTxid(params?: {}): Promise<implicitReturnType>;
    privateDeleteOrder(params?: {}): Promise<implicitReturnType>;
    privateDeleteOrdersOpen(params?: {}): Promise<implicitReturnType>;
    privateDeleteOrdersUuids(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/upbit.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 60
- Code lines: 59
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
ts-node js/src/abstract/upbit.d.ts
```

