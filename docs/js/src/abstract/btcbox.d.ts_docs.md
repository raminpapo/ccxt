# Documentation: js/src/abstract/btcbox.d.ts

## File Metadata

- **Path**: `js/src/abstract/btcbox.d.ts`
- **Size**: 947 bytes
- **Lines**: 19
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetDepth(params?: {}): Promise<implicitReturnType>;
    publicGetOrders(params?: {}): Promise<implicitReturnType>;
    publicGetTicker(params?: {}): Promise<implicitReturnType>;
    publicGetTickers(params?: {}): Promise<implicitReturnType>;
    privatePostBalance(params?: {}): Promise<implicitReturnType>;
    privatePostTradeAdd(params?: {}): Promise<implicitReturnType>;
    privatePostTradeCancel(params?: {}): Promise<implicitReturnType>;
    privatePostTradeList(params?: {}): Promise<implicitReturnType>;
    privatePostTradeView(params?: {}): Promise<implicitReturnType>;
    privatePostWallet(params?: {}): Promise<implicitReturnType>;
    webApiGetAjaxCoinCoinInfo(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/btcbox.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 18
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
ts-node js/src/abstract/btcbox.d.ts
```

