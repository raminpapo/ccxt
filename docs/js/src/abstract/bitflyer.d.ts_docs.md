# Documentation: js/src/abstract/bitflyer.d.ts

## File Metadata

- **Path**: `js/src/abstract/bitflyer.d.ts`
- **Size**: 2,708 bytes
- **Lines**: 43
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import { implicitReturnType } from '../base/types.js';
import { Exchange as _Exchange } from '../base/Exchange.js';
interface Exchange {
    publicGetGetmarketsUsa(params?: {}): Promise<implicitReturnType>;
    publicGetGetmarketsEu(params?: {}): Promise<implicitReturnType>;
    publicGetGetmarkets(params?: {}): Promise<implicitReturnType>;
    publicGetGetboard(params?: {}): Promise<implicitReturnType>;
    publicGetGetticker(params?: {}): Promise<implicitReturnType>;
    publicGetGetexecutions(params?: {}): Promise<implicitReturnType>;
    publicGetGethealth(params?: {}): Promise<implicitReturnType>;
    publicGetGetboardstate(params?: {}): Promise<implicitReturnType>;
    publicGetGetchats(params?: {}): Promise<implicitReturnType>;
    publicGetGetfundingrate(params?: {}): Promise<implicitReturnType>;
    privateGetGetpermissions(params?: {}): Promise<implicitReturnType>;
    privateGetGetbalance(params?: {}): Promise<implicitReturnType>;
    privateGetGetbalancehistory(params?: {}): Promise<implicitReturnType>;
    privateGetGetcollateral(params?: {}): Promise<implicitReturnType>;
    privateGetGetcollateralhistory(params?: {}): Promise<implicitReturnType>;
    privateGetGetcollateralaccounts(params?: {}): Promise<implicitReturnType>;
    privateGetGetaddresses(params?: {}): Promise<implicitReturnType>;
    privateGetGetcoinins(params?: {}): Promise<implicitReturnType>;
    privateGetGetcoinouts(params?: {}): Promise<implicitReturnType>;
    privateGetGetbankaccounts(params?: {}): Promise<implicitReturnType>;
    privateGetGetdeposits(params?: {}): Promise<implicitReturnType>;
    privateGetGetwithdrawals(params?: {}): Promise<implicitReturnType>;
    privateGetGetchildorders(params?: {}): Promise<implicitReturnType>;
    privateGetGetparentorders(params?: {}): Promise<implicitReturnType>;
    privateGetGetparentorder(params?: {}): Promise<implicitReturnType>;
    privateGetGetexecutions(params?: {}): Promise<implicitReturnType>;
    privateGetGetpositions(params?: {}): Promise<implicitReturnType>;
    privateGetGettradingcommission(params?: {}): Promise<implicitReturnType>;
    privatePostSendcoin(params?: {}): Promise<implicitReturnType>;
    privatePostWithdraw(params?: {}): Promise<implicitReturnType>;
    privatePostSendchildorder(params?: {}): Promise<implicitReturnType>;
    privatePostCancelchildorder(params?: {}): Promise<implicitReturnType>;
    privatePostSendparentorder(params?: {}): Promise<implicitReturnType>;
    privatePostCancelparentorder(params?: {}): Promise<implicitReturnType>;
    privatePostCancelallchildorders(params?: {}): Promise<implicitReturnType>;
}
declare abstract class Exchange extends _Exchange {
}
export default Exchange;

```

## High-Level Overview

This is a TypeScript file located at `js/src/abstract/bitflyer.d.ts`.

**Classes defined**: Exchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 43
- Code lines: 42
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
ts-node js/src/abstract/bitflyer.d.ts
```

