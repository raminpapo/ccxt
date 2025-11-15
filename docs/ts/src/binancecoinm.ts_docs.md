# Documentation: ts/src/binancecoinm.ts

## File Metadata

- **Path**: `ts/src/binancecoinm.ts`
- **Size**: 1,758 bytes
- **Lines**: 52
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

//  ---------------------------------------------------------------------------

import binance from './binance.js';

//  ---------------------------------------------------------------------------

export default class binancecoinm extends binance {
    describe (): any {
        return this.deepExtend (super.describe (), {
            'id': 'binancecoinm',
            'name': 'Binance COIN-M',
            'urls': {
                'logo': 'https://github.com/user-attachments/assets/387cfc4e-5f33-48cd-8f5c-cd4854dabf0c',
                'doc': [
                    'https://binance-docs.github.io/apidocs/delivery/en/',
                    'https://binance-docs.github.io/apidocs/spot/en',
                    'https://developers.binance.com/en',
                ],
            },
            'has': {
                'CORS': undefined,
                'spot': false,
                'margin': false,
                'swap': true,
                'future': true,
                'option': undefined,
                'createStopMarketOrder': true,
            },
            'options': {
                'fetchMarkets': {
                    'types': [
                        'inverse',
                    ],
                },
                'defaultSubType': 'inverse',
                'leverageBrackets': undefined,
            },
        });
    }

    async transferIn (code: string, amount, params = {}) {
        // transfer from spot wallet to coinm futures wallet
        return await this.futuresTransfer (code, amount, 3, params);
    }

    async transferOut (code: string, amount, params = {}) {
        // transfer from coinm futures wallet to spot wallet
        return await this.futuresTransfer (code, amount, 4, params);
    }
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/binancecoinm.ts`.

**Classes defined**: binancecoinm

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 52
- Code lines: 41
- Comment lines: 4
- Blank lines: 7

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./binance.js` (imported)
- `./binance.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/binancecoinm.ts
```

