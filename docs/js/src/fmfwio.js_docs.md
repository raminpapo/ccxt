# Documentation: js/src/fmfwio.js

## File Metadata

- **Path**: `js/src/fmfwio.js`
- **Size**: 1,167 bytes
- **Lines**: 30
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
//  ----------------------------------------------------------------------------
import hitbtc from './hitbtc.js';
//  ----------------------------------------------------------------------------
export default class fmfwio extends hitbtc {
    describe() {
        return this.deepExtend(super.describe(), {
            'id': 'fmfwio',
            'name': 'FMFW.io',
            'countries': ['KN'],
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
                    'maker': this.parseNumber('0.005'),
                    'taker': this.parseNumber('0.005'),
                },
            },
        });
    }
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/fmfwio.js`.

**Classes defined**: fmfwio

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 27
- Comment lines: 2
- Blank lines: 1

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

**To execute this JavaScript file:**

```bash
node js/src/fmfwio.js
```

