# Documentation: js/src/abstract/novadax.d.ts

## File Metadata

- **Path**: `js/src/abstract/novadax.d.ts`
- **Size**: 2,045 bytes
- **Lines**: 33
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetCommonSymbol(params?: {}): Promise<implicitReturnType>;
    publicGetCommonSymbols(params?: {}): Promise<implicitReturnType>;
    publicGetCommonTimestamp(params?: {}): Promise<implicitReturnType>;
    publicGetMarketTickers(params?: {}): Promise<implicitReturnType>;
    publicGetMarketTicker(params?: {}): Promise<implicitReturnType>;
    publicGetMarketDepth(params?: {}): Promise<implicitReturnType>;
    publicGetMarketTrades(params?: {}): Promise<implicitReturnType>;
    publicGetMarketKlineHistory(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersGet(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersList(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersFill(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersFills(params?: {}): Promise<implicitReturnType>;
    privateGetAccountGetBalance(params?: {}): Promise<implicitReturnType>;
    privateGetAccountSubs(params?: {}): Promise<implicitReturnType>;
    privateGetAccountSubsBalance(params?: {}): Promise<implicitReturnType>;
    privateGetAccountSubsTransferRecord(params?: {}): Promise<implicitReturnType>;
    privateGetWalletQueryDepositWithdraw(params?: {}): Promise<implicitReturnType>;
    privatePostOrdersCreate(params?: {}): Promise<implicitReturnType>;
    privatePostOrdersBatchCreate(params?: {}): Promise<implicitReturnType>;
    privatePostOrdersCancel(params?: {}): Promise<implicitReturnType>;
    privatePostOrdersBatchCancel(params?: {}): Promise<implicitReturnType>;
    privatePostOrdersCancelBySymbol(params?: {}): Promise<implicitReturnType>;
    privatePostAccountSubsTransfer(params?: {}): Promise<implicitReturnType>;
    privatePostWalletWithdrawCoin(params?: {}): Promise<implicitReturnType>;
    privatePostAccountWithdrawCoin(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/novadax.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 32
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
ts-node js/src/abstract/novadax.d.ts
```

