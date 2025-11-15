# Documentation: js/src/pro/binanceusdm.js

## File Metadata

- **Path**: `js/src/pro/binanceusdm.js`
- **Size**: 1,338 bytes
- **Lines**: 32
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
//  ---------------------------------------------------------------------------
import binance from './binance.js';
import { InvalidOrder } from '../base/errors.js';
// ---------------------------------------------------------------------------
export default class binanceusdm extends binance {
    describe() {
        return this.deepExtend(super.describe(), {
            'id': 'binanceusdm',
            'name': 'Binance USDⓈ-M',
            'urls': {
                'logo': 'https://user-images.githubusercontent.com/1294454/117738721-668c8d80-b205-11eb-8c49-3fad84c4a07f.jpg',
                'doc': 'https://developers.binance.com/en',
            },
            'options': {
                'fetchMarkets': {
                    'types': ['linear'],
                },
                'defaultSubType': 'linear',
            },
            // https://binance-docs.github.io/apidocs/futures/en/#error-codes
            // https://developers.binance.com/docs/derivatives/usds-margined-futures/error-code
            'exceptions': {
                'exact': {
                    '-5021': InvalidOrder,
                    '-5022': InvalidOrder,
                    '-5028': InvalidOrder, // {"code":-5028,"msg":"Timestamp for this request is outside of the ME recvWindow."}
                },
            },
        });
    }
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/pro/binanceusdm.js`.

**Classes defined**: binanceusdm

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 27
- Comment lines: 4
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./binance.js` (imported)
- `../base/errors.js` (imported)
- `./binance.js` (referenced)
- `../base/errors.js` (referenced)
- `https://user-images.githubusercontent.com/1294454/117738721-668c8d80-b205-11eb-8c49-3fad84c4a07f.jpg` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/pro/binanceusdm.js
```

