# Documentation: js/src/abstract/krakenfutures.d.ts

## File Metadata

- **Path**: `js/src/abstract/krakenfutures.d.ts`
- **Size**: 2,941 bytes
- **Lines**: 46
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetFeeschedules(params?: {}): Promise<implicitReturnType>;
    publicGetInstruments(params?: {}): Promise<implicitReturnType>;
    publicGetOrderbook(params?: {}): Promise<implicitReturnType>;
    publicGetTickers(params?: {}): Promise<implicitReturnType>;
    publicGetHistory(params?: {}): Promise<implicitReturnType>;
    publicGetHistoricalfundingrates(params?: {}): Promise<implicitReturnType>;
    privateGetFeeschedulesVolumes(params?: {}): Promise<implicitReturnType>;
    privateGetOpenpositions(params?: {}): Promise<implicitReturnType>;
    privateGetNotifications(params?: {}): Promise<implicitReturnType>;
    privateGetAccounts(params?: {}): Promise<implicitReturnType>;
    privateGetOpenorders(params?: {}): Promise<implicitReturnType>;
    privateGetRecentorders(params?: {}): Promise<implicitReturnType>;
    privateGetFills(params?: {}): Promise<implicitReturnType>;
    privateGetTransfers(params?: {}): Promise<implicitReturnType>;
    privateGetLeveragepreferences(params?: {}): Promise<implicitReturnType>;
    privateGetPnlpreferences(params?: {}): Promise<implicitReturnType>;
    privateGetAssignmentprogramCurrent(params?: {}): Promise<implicitReturnType>;
    privateGetAssignmentprogramHistory(params?: {}): Promise<implicitReturnType>;
    privatePostSendorder(params?: {}): Promise<implicitReturnType>;
    privatePostEditorder(params?: {}): Promise<implicitReturnType>;
    privatePostCancelorder(params?: {}): Promise<implicitReturnType>;
    privatePostTransfer(params?: {}): Promise<implicitReturnType>;
    privatePostBatchorder(params?: {}): Promise<implicitReturnType>;
    privatePostCancelallorders(params?: {}): Promise<implicitReturnType>;
    privatePostCancelallordersafter(params?: {}): Promise<implicitReturnType>;
    privatePostWithdrawal(params?: {}): Promise<implicitReturnType>;
    privatePostAssignmentprogramAdd(params?: {}): Promise<implicitReturnType>;
    privatePostAssignmentprogramDelete(params?: {}): Promise<implicitReturnType>;
    privatePutLeveragepreferences(params?: {}): Promise<implicitReturnType>;
    privatePutPnlpreferences(params?: {}): Promise<implicitReturnType>;
    chartsGetPriceTypeSymbolInterval(params?: {}): Promise<implicitReturnType>;
    historyGetOrders(params?: {}): Promise<implicitReturnType>;
    historyGetExecutions(params?: {}): Promise<implicitReturnType>;
    historyGetTriggers(params?: {}): Promise<implicitReturnType>;
    historyGetAccountlogcsv(params?: {}): Promise<implicitReturnType>;
    historyGetAccountLog(params?: {}): Promise<implicitReturnType>;
    historyGetMarketSymbolOrders(params?: {}): Promise<implicitReturnType>;
    historyGetMarketSymbolExecutions(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/krakenfutures.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 46
- Code lines: 45
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
ts-node js/src/abstract/krakenfutures.d.ts
```

