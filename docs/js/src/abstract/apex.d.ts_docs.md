# Documentation: js/src/abstract/apex.d.ts

## File Metadata

- **Path**: `js/src/abstract/apex.d.ts`
- **Size**: 2,124 bytes
- **Lines**: 35
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetV3Symbols(params?: {}): Promise<implicitReturnType>;
    publicGetV3HistoryFunding(params?: {}): Promise<implicitReturnType>;
    publicGetV3Ticker(params?: {}): Promise<implicitReturnType>;
    publicGetV3Klines(params?: {}): Promise<implicitReturnType>;
    publicGetV3Trades(params?: {}): Promise<implicitReturnType>;
    publicGetV3Depth(params?: {}): Promise<implicitReturnType>;
    publicGetV3Time(params?: {}): Promise<implicitReturnType>;
    publicGetV3DataAllTickerInfo(params?: {}): Promise<implicitReturnType>;
    privateGetV3Account(params?: {}): Promise<implicitReturnType>;
    privateGetV3AccountBalance(params?: {}): Promise<implicitReturnType>;
    privateGetV3Fills(params?: {}): Promise<implicitReturnType>;
    privateGetV3OrderFills(params?: {}): Promise<implicitReturnType>;
    privateGetV3Order(params?: {}): Promise<implicitReturnType>;
    privateGetV3HistoryOrders(params?: {}): Promise<implicitReturnType>;
    privateGetV3OrderByClientOrderId(params?: {}): Promise<implicitReturnType>;
    privateGetV3Funding(params?: {}): Promise<implicitReturnType>;
    privateGetV3HistoricalPnl(params?: {}): Promise<implicitReturnType>;
    privateGetV3OpenOrders(params?: {}): Promise<implicitReturnType>;
    privateGetV3Transfers(params?: {}): Promise<implicitReturnType>;
    privateGetV3Transfer(params?: {}): Promise<implicitReturnType>;
    privatePostV3DeleteOpenOrders(params?: {}): Promise<implicitReturnType>;
    privatePostV3DeleteClientOrderId(params?: {}): Promise<implicitReturnType>;
    privatePostV3DeleteOrder(params?: {}): Promise<implicitReturnType>;
    privatePostV3Order(params?: {}): Promise<implicitReturnType>;
    privatePostV3SetInitialMarginRate(params?: {}): Promise<implicitReturnType>;
    privatePostV3TransferOut(params?: {}): Promise<implicitReturnType>;
    privatePostV3ContractTransferOut(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/apex.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 34
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
ts-node js/src/abstract/apex.d.ts
```

