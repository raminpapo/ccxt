# Documentation: ts/src/myokx.ts

## File Metadata

- **Path**: `ts/src/myokx.ts`
- **Size**: 1,708 bytes
- **Lines**: 53
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

// ---------------------------------------------------------------------------

import okx from './okx.js';

// ---------------------------------------------------------------------------

export default class myokx extends okx {
    describe (): any {
        return this.deepExtend (super.describe (), {
            'id': 'myokx',
            'name': 'MyOKX (EEA)',
            'certified': false,
            'pro': true,
            'hostname': 'eea.okx.com',
            'urls': {
                'logo': 'https://user-images.githubusercontent.com/1294454/152485636-38b19e4a-bece-4dec-979a-5982859ffc04.jpg',
                'api': {
                    'rest': 'https://{hostname}',
                },
                'www': 'https://my.okx.com',
                'doc': 'https://my.okx.com/docs-v5/en/#overview',
                'fees': 'https://my.okx.com/pages/products/fees.html',
                'referral': {
                    'url': 'https://www.my.okx.com/join/CCXT2023',
                    'discount': 0.2,
                },
                'test': {
                    'rest': 'https://{hostname}',
                },
            },
            'has': {
                'CORS': undefined,
                'spot': true,
                'margin': undefined,
                'swap': false,
                'future': false,
                'option': false,
            },
            'features': {
                'swap': {
                    'linear': undefined,
                    'inverse': undefined,
                },
                'future': {
                    'linear': undefined,
                    'inverse': undefined,
                },
            },
        });
    }
}

```

## High-Level Overview

This is a TypeScript file located at `ts/src/myokx.ts`.

**Classes defined**: myokx

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 53
- Code lines: 46
- Comment lines: 2
- Blank lines: 5

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./okx.js` (imported)
- `https://my.okx.com` (referenced)
- `https://my.okx.com/pages/products/fees.html` (referenced)
- `https://user-images.githubusercontent.com/1294454/152485636-38b19e4a-bece-4dec-979a-5982859ffc04.jpg` (referenced)
- `./okx.js` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/myokx.ts
```

