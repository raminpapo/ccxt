# Documentation: ts/src/bequant.ts

## File Metadata

- **Path**: `ts/src/bequant.ts`
- **Size**: 1,120 bytes
- **Lines**: 33
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

// ---------------------------------------------------------------------------

import hitbtc from './hitbtc.js';
// ---------------------------------------------------------------------------

export default class bequant extends hitbtc {
    describe (): any {
        return this.deepExtend (super.describe (), {
            'id': 'bequant',
            'name': 'Bequant',
            'pro': true,
            'countries': [ 'MT' ], // Malta
            'urls': {
                'logo': 'https://github.com/user-attachments/assets/0583ef1f-29fe-4b7c-8189-63565a0e2867',
                'api': {
                    // v3
                    'public': 'https://api.bequant.io/api/3',
                    'private': 'https://api.bequant.io/api/3',
                },
                'www': 'https://bequant.io',
                'doc': [
                    'https://api.bequant.io/',
                ],
                'fees': [
                    'https://bequant.io/fees-and-limits',
                ],
                'referral': 'https://bequant.io/referral/dd104e3bee7634ec',
            },
        });
    }
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/bequant.ts`.

**Classes defined**: bequant

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 26
- Comment lines: 3
- Blank lines: 4

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./hitbtc.js` (imported)
- `https://bequant.io` (referenced)
- `./hitbtc.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/bequant.ts
```

