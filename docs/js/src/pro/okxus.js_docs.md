# Documentation: js/src/pro/okxus.js

## File Metadata

- **Path**: `js/src/pro/okxus.js`
- **Size**: 1,182 bytes
- **Lines**: 34
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
//  ---------------------------------------------------------------------------
import okx from './okx.js';
// ---------------------------------------------------------------------------
export default class okxus extends okx {
    describe() {
        return this.deepExtend(super.describe(), {
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

This is a JavaScript file located at `js/src/pro/okxus.js`.

**Classes defined**: okxus

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 31
- Comment lines: 2
- Blank lines: 1

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

**To execute this JavaScript file:**

```bash
node js/src/pro/okxus.js
```

