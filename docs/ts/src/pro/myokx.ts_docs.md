# Documentation: ts/src/pro/myokx.ts

## File Metadata

- **Path**: `ts/src/pro/myokx.ts`
- **Size**: 1,196 bytes
- **Lines**: 38
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

//  ---------------------------------------------------------------------------

import okx from './okx.js';

// ---------------------------------------------------------------------------

export default class myokx extends okx {
    describe (): any {
        return this.deepExtend (super.describe (), {
            'id': 'myokx',
            'name': 'MyOKX (EEA)',
            'hostname': 'eea.okx.com',
            'urls': {
                'api': {
                    'rest': 'https://{hostname}',
                    'ws': 'wss://wseea.okx.com:8443/ws/v5',
                },
                'www': 'https://my.okx.com',
                'doc': 'https://my.okx.com/docs-v5/en/#overview',
                'fees': 'https://my.okx.com/pages/products/fees.html',
                'referral': {
                    'url': 'https://www.my.okx.com/join/CCXT2023',
                    'discount': 0.2,
                },
                'test': {
                    'ws': 'wss://wseeapap.okx.com:8443/ws/v5',
                },
            },
            'has': {
                'swap': false,
                'future': false,
                'option': false,
            },
        });
    }
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/pro/myokx.ts`.

**Classes defined**: myokx

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 38
- Code lines: 31
- Comment lines: 2
- Blank lines: 5

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./okx.js` (imported)
- `https://my.okx.com/pages/products/fees.html` (referenced)
- `./okx.js` (referenced)
- `https://my.okx.com` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/pro/myokx.ts
```

