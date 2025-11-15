# Documentation: ts/src/fmfwio.ts

## File Metadata

- **Path**: `ts/src/fmfwio.ts`
- **Size**: 1,183 bytes
- **Lines**: 34
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

//  ----------------------------------------------------------------------------

import hitbtc from './hitbtc.js';

//  ----------------------------------------------------------------------------

export default class fmfwio extends hitbtc {
    describe (): any {
        return this.deepExtend (super.describe (), {
            'id': 'fmfwio',
            'name': 'FMFW.io',
            'countries': [ 'KN' ],
            'urls': {
                'logo': 'https://user-images.githubusercontent.com/1294454/159177712-b685b40c-5269-4cea-ac83-f7894c49525d.jpg',
                'api': {
                    'public': 'https://api.fmfw.io/api/3',
                    'private': 'https://api.fmfw.io/api/3',
                },
                'www': 'https://fmfw.io',
                'doc': 'https://api.fmfw.io/',
                'fees': 'https://fmfw.io/fees-and-limits',
                'referral': 'https://fmfw.io/referral/da948b21d6c92d69',
            },
            'fees': {
                'trading': {
                    'maker': this.parseNumber ('0.005'),
                    'taker': this.parseNumber ('0.005'),
                },
            },
        });
    }
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/fmfwio.ts`.

**Classes defined**: fmfwio

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 27
- Comment lines: 2
- Blank lines: 5

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./hitbtc.js` (imported)
- `https://user-images.githubusercontent.com/1294454/159177712-b685b40c-5269-4cea-ac83-f7894c49525d.jpg` (referenced)
- `./hitbtc.js` (referenced)
- `https://fmfw.io` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/fmfwio.ts
```

