# Documentation: js/src/binanceusdm.js

## File Metadata

- **Path**: `js/src/binanceusdm.js`
- **Size**: 2,408 bytes
- **Lines**: 58
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
//  ---------------------------------------------------------------------------
import binance from './binance.js';
import { InvalidOrder } from './base/errors.js';
//  ---------------------------------------------------------------------------
export default class binanceusdm extends binance {
    describe() {
        return this.deepExtend(super.describe(), {
            'id': 'binanceusdm',
            'name': 'Binance USDⓈ-M',
            'urls': {
                'logo': 'https://github.com/user-attachments/assets/871cbea7-eebb-4b28-b260-c1c91df0487a',
                'doc': [
                    'https://binance-docs.github.io/apidocs/futures/en/',
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
                    'types': ['linear'],
                },
                'defaultSubType': 'linear',
                // https://www.binance.com/en/support/faq/360033162192
                // tier amount, maintenance margin, initial margin,
                'leverageBrackets': undefined,
                'marginTypes': {},
                'marginModes': {},
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
    async transferIn(code, amount, params = {}) {
        // transfer from spot wallet to usdm futures wallet
        return await this.futuresTransfer(code, amount, 1, params);
    }
    async transferOut(code, amount, params = {}) {
        // transfer from usdm futures wallet to spot wallet
        return await this.futuresTransfer(code, amount, 2, params);
    }
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/binanceusdm.js`.

**Classes defined**: binanceusdm

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 58
- Code lines: 49
- Comment lines: 8
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./binance.js` (imported)
- `./base/errors.js` (imported)
- `./binance.js` (referenced)
- `./base/errors.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/binanceusdm.js
```

