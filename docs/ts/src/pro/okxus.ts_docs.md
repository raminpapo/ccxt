# Documentation: ts/src/pro/okxus.ts

## File Metadata

- **Path**: `ts/src/pro/okxus.ts`
- **Size**: 1,194 bytes
- **Lines**: 38
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript

//  ---------------------------------------------------------------------------

import okx from './okx.js';

// ---------------------------------------------------------------------------

export default class okxus extends okx {
    describe (): any {
        return this.deepExtend (super.describe (), {
            'id': 'okxus',
            'name': 'OKX (US)',
            'hostname': 'us.okx.com',
            'urls': {
                'api': {
                    'rest': 'https://{hostname}',
                    'ws': 'wss://wsus.okx.com:8443/ws/v5',
                },
                'www': 'https://app.okx.com',
                'doc': 'https://app.okx.com/docs-v5/en/#overview',
                'fees': 'https://app.okx.com/pages/products/fees.html',
                'referral': {
                    'url': 'https://www.app.okx.com/join/CCXT2023',
                    'discount': 0.2,
                },
                'test': {
                    'ws': 'wss://wsuspap.okx.com:8443/ws/v5',
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

This is a TypeScript file located at `ts/src/pro/okxus.ts`.

**Classes defined**: okxus

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
- `https://app.okx.com` (referenced)
- `./okx.js` (referenced)
- `https://app.okx.com/pages/products/fees.html` (referenced)



## Testing & Execution

**To execute this TypeScript file:**

```bash
ts-node ts/src/pro/okxus.ts
```

