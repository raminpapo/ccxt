# Documentation: js/src/abstract/hollaex.d.ts

## File Metadata

- **Path**: `js/src/abstract/hollaex.d.ts`
- **Size**: 2,136 bytes
- **Lines**: 37
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetHealth(params?: {}): Promise<implicitReturnType>;
    publicGetConstants(params?: {}): Promise<implicitReturnType>;
    publicGetKit(params?: {}): Promise<implicitReturnType>;
    publicGetTiers(params?: {}): Promise<implicitReturnType>;
    publicGetTicker(params?: {}): Promise<implicitReturnType>;
    publicGetTickers(params?: {}): Promise<implicitReturnType>;
    publicGetOrderbook(params?: {}): Promise<implicitReturnType>;
    publicGetOrderbooks(params?: {}): Promise<implicitReturnType>;
    publicGetTrades(params?: {}): Promise<implicitReturnType>;
    publicGetChart(params?: {}): Promise<implicitReturnType>;
    publicGetCharts(params?: {}): Promise<implicitReturnType>;
    publicGetMinicharts(params?: {}): Promise<implicitReturnType>;
    publicGetOraclePrices(params?: {}): Promise<implicitReturnType>;
    publicGetQuickTrade(params?: {}): Promise<implicitReturnType>;
    publicGetUdfConfig(params?: {}): Promise<implicitReturnType>;
    publicGetUdfHistory(params?: {}): Promise<implicitReturnType>;
    publicGetUdfSymbols(params?: {}): Promise<implicitReturnType>;
    privateGetUser(params?: {}): Promise<implicitReturnType>;
    privateGetUserBalance(params?: {}): Promise<implicitReturnType>;
    privateGetUserDeposits(params?: {}): Promise<implicitReturnType>;
    privateGetUserWithdrawals(params?: {}): Promise<implicitReturnType>;
    privateGetUserWithdrawalFee(params?: {}): Promise<implicitReturnType>;
    privateGetUserTrades(params?: {}): Promise<implicitReturnType>;
    privateGetOrders(params?: {}): Promise<implicitReturnType>;
    privateGetOrder(params?: {}): Promise<implicitReturnType>;
    privatePostUserWithdrawal(params?: {}): Promise<implicitReturnType>;
    privatePostOrder(params?: {}): Promise<implicitReturnType>;
    privateDeleteOrderAll(params?: {}): Promise<implicitReturnType>;
    privateDeleteOrder(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/hollaex.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 36
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
ts-node js/src/abstract/hollaex.d.ts
```

