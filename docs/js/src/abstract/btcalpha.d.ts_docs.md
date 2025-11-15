# Documentation: js/src/abstract/btcalpha.d.ts

## File Metadata

- **Path**: `js/src/abstract/btcalpha.d.ts`
- **Size**: 1,160 bytes
- **Lines**: 22
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetCurrencies(params?: {}): Promise<implicitReturnType>;
    publicGetPairs(params?: {}): Promise<implicitReturnType>;
    publicGetOrderbookPairName(params?: {}): Promise<implicitReturnType>;
    publicGetExchanges(params?: {}): Promise<implicitReturnType>;
    publicGetChartsPairTypeChart(params?: {}): Promise<implicitReturnType>;
    publicGetTicker(params?: {}): Promise<implicitReturnType>;
    privateGetWallets(params?: {}): Promise<implicitReturnType>;
    privateGetOrdersOwn(params?: {}): Promise<implicitReturnType>;
    privateGetOrderId(params?: {}): Promise<implicitReturnType>;
    privateGetExchangesOwn(params?: {}): Promise<implicitReturnType>;
    privateGetDeposits(params?: {}): Promise<implicitReturnType>;
    privateGetWithdraws(params?: {}): Promise<implicitReturnType>;
    privatePostOrder(params?: {}): Promise<implicitReturnType>;
    privatePostOrderCancel(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/btcalpha.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 21
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
ts-node js/src/abstract/btcalpha.d.ts
```

