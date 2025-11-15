# Documentation: ts/src/pro/bequant.ts

## File Metadata

- **Path**: `ts/src/pro/bequant.ts`
- **Size**: 1,545 bytes
- **Lines**: 41
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

//  ---------------------------------------------------------------------------

import hitbtc from './hitbtc.js';
import hitbtcRest from '../hitbtc.js';
import bequantRest from '../bequant.js';

// ---------------------------------------------------------------------------

export default class bequant extends hitbtc {
    describe (): any {
        // eslint-disable-next-line new-cap
        const describeExtended = this.getDescribeForExtendedWsExchange (new bequantRest (), new hitbtcRest (), super.describe ());
        return this.deepExtend (describeExtended, {
            'id': 'bequant',
            'name': 'Bequant',
            'countries': [ 'MT' ], // Malta
            'pro': true,
            'urls': {
                'logo': 'https://user-images.githubusercontent.com/1294454/55248342-a75dfe00-525a-11e9-8aa2-05e9dca943c6.jpg',
                'api': {
                    'public': 'https://api.bequant.io/api/3',
                    'private': 'https://api.bequant.io/api/3',
                    'ws': {
                        'public': 'wss://api.bequant.io/api/3/ws/public',
                        'private': 'wss://api.bequant.io/api/3/ws/trading',
                    },
                },
                'www': 'https://bequant.io',
                'doc': [
                    'https://api.bequant.io/',
                ],
                'fees': [
                    'https://bequant.io/fees-and-limits',
                ],
                'referral': 'https://bequant.io',
            },
        });
    }
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/pro/bequant.ts`.

**Classes defined**: bequant

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 33
- Comment lines: 3
- Blank lines: 5

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `../hitbtc.js` (imported)
- `./hitbtc.js` (imported)
- `../bequant.js` (imported)
- `https://bequant.io` (referenced)
- `./hitbtc.js` (referenced)
- `../hitbtc.js` (referenced)
- `https://user-images.githubusercontent.com/1294454/55248342-a75dfe00-525a-11e9-8aa2-05e9dca943c6.jpg` (referenced)
- `../bequant.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/pro/bequant.ts
```

