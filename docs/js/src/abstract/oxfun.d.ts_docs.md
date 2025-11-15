# Documentation: js/src/abstract/oxfun.d.ts

## File Metadata

- **Path**: `js/src/abstract/oxfun.d.ts`
- **Size**: 2,332 bytes
- **Lines**: 38
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetV3Markets(params?: {}): Promise<implicitReturnType>;
    publicGetV3Assets(params?: {}): Promise<implicitReturnType>;
    publicGetV3Tickers(params?: {}): Promise<implicitReturnType>;
    publicGetV3FundingEstimates(params?: {}): Promise<implicitReturnType>;
    publicGetV3Candles(params?: {}): Promise<implicitReturnType>;
    publicGetV3Depth(params?: {}): Promise<implicitReturnType>;
    publicGetV3MarketsOperational(params?: {}): Promise<implicitReturnType>;
    publicGetV3ExchangeTrades(params?: {}): Promise<implicitReturnType>;
    publicGetV3FundingRates(params?: {}): Promise<implicitReturnType>;
    publicGetV3LeverageTiers(params?: {}): Promise<implicitReturnType>;
    privateGetV3Account(params?: {}): Promise<implicitReturnType>;
    privateGetV3AccountNames(params?: {}): Promise<implicitReturnType>;
    privateGetV3Wallet(params?: {}): Promise<implicitReturnType>;
    privateGetV3Transfer(params?: {}): Promise<implicitReturnType>;
    privateGetV3Balances(params?: {}): Promise<implicitReturnType>;
    privateGetV3Positions(params?: {}): Promise<implicitReturnType>;
    privateGetV3Funding(params?: {}): Promise<implicitReturnType>;
    privateGetV3DepositAddresses(params?: {}): Promise<implicitReturnType>;
    privateGetV3Deposit(params?: {}): Promise<implicitReturnType>;
    privateGetV3WithdrawalAddresses(params?: {}): Promise<implicitReturnType>;
    privateGetV3Withdrawal(params?: {}): Promise<implicitReturnType>;
    privateGetV3WithdrawalFees(params?: {}): Promise<implicitReturnType>;
    privateGetV3OrdersStatus(params?: {}): Promise<implicitReturnType>;
    privateGetV3OrdersWorking(params?: {}): Promise<implicitReturnType>;
    privateGetV3Trades(params?: {}): Promise<implicitReturnType>;
    privatePostV3Transfer(params?: {}): Promise<implicitReturnType>;
    privatePostV3Withdrawal(params?: {}): Promise<implicitReturnType>;
    privatePostV3OrdersPlace(params?: {}): Promise<implicitReturnType>;
    privateDeleteV3OrdersCancel(params?: {}): Promise<implicitReturnType>;
    privateDeleteV3OrdersCancelAll(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/oxfun.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 38
- Code lines: 37
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
ts-node js/src/abstract/oxfun.d.ts
```

