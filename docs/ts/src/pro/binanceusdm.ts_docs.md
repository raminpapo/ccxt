# Documentation: ts/src/pro/binanceusdm.ts

## File Metadata

- **Path**: `ts/src/pro/binanceusdm.ts`
- **Size**: 1,574 bytes
- **Lines**: 36
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

//  ---------------------------------------------------------------------------

import binance from './binance.js';
import { InvalidOrder } from '../base/errors.js';

// ---------------------------------------------------------------------------

export default class binanceusdm extends binance {
    describe (): any {
        return this.deepExtend (super.describe (), {
            'id': 'binanceusdm',
            'name': 'Binance USDⓈ-M',
            'urls': {
                'logo': 'https://user-images.githubusercontent.com/1294454/117738721-668c8d80-b205-11eb-8c49-3fad84c4a07f.jpg',
                'doc': 'https://developers.binance.com/en',
            },
            'options': {
                'fetchMarkets': {
                    'types': [ 'linear' ],
                },
                'defaultSubType': 'linear',
            },
            // https://binance-docs.github.io/apidocs/futures/en/#error-codes
            // https://developers.binance.com/docs/derivatives/usds-margined-futures/error-code
            'exceptions': {
                'exact': {
                    '-5021': InvalidOrder, // {"code":-5021,"msg":"Due to the order could not be filled immediately, the FOK order has been rejected."}
                    '-5022': InvalidOrder, // {"code":-5022,"msg":"Due to the order could not be executed as maker, the Post Only order will be rejected."}
                    '-5028': InvalidOrder, // {"code":-5028,"msg":"Timestamp for this request is outside of the ME recvWindow."}
                },
            },
        });
    }
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/pro/binanceusdm.ts`.

**Classes defined**: binanceusdm

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 27
- Comment lines: 4
- Blank lines: 5

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./binance.js` (imported)
- `../base/errors.js` (imported)
- `./binance.js` (referenced)
- `../base/errors.js` (referenced)
- `https://user-images.githubusercontent.com/1294454/117738721-668c8d80-b205-11eb-8c49-3fad84c4a07f.jpg` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/pro/binanceusdm.ts
```

