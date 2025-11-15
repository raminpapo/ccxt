# Documentation: ts/src/pro/binancecoinm.ts

## File Metadata

- **Path**: `ts/src/pro/binancecoinm.ts`
- **Size**: 1,097 bytes
- **Lines**: 31
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

//  ---------------------------------------------------------------------------

import binance from './binance.js';
import binancecoinmRest from '../binancecoinm.js';

// ---------------------------------------------------------------------------

export default class binancecoinm extends binance {
    describe (): any {
        // eslint-disable-next-line new-cap
        const restInstance = new binancecoinmRest ();
        const restDescribe = restInstance.describe ();
        const extended = this.deepExtend (super.describe (), restDescribe);
        return this.deepExtend (extended, {
            'id': 'binancecoinm',
            'name': 'Binance COIN-M',
            'urls': {
                'logo': 'https://user-images.githubusercontent.com/1294454/117738721-668c8d80-b205-11eb-8c49-3fad84c4a07f.jpg',
                'doc': 'https://developers.binance.com/en',
            },
            'options': {
                'fetchMarkets': {
                    'types': [ 'inverse' ],
                },
                'defaultSubType': 'inverse',
            },
        });
    }
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/pro/binancecoinm.ts`.

**Classes defined**: binancecoinm

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 23
- Comment lines: 3
- Blank lines: 5

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./binance.js` (imported)
- `../binancecoinm.js` (imported)
- `./binance.js` (referenced)
- `https://user-images.githubusercontent.com/1294454/117738721-668c8d80-b205-11eb-8c49-3fad84c4a07f.jpg` (referenced)
- `../binancecoinm.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/pro/binancecoinm.ts
```

