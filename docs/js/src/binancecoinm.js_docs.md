# Documentation: js/src/binancecoinm.js

## File Metadata

- **Path**: `js/src/binancecoinm.js`
- **Size**: 1,724 bytes
- **Lines**: 46
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
//  ---------------------------------------------------------------------------
import binance from './binance.js';
//  ---------------------------------------------------------------------------
export default class binancecoinm extends binance {
    describe() {
        return this.deepExtend(super.describe(), {
            'id': 'binancecoinm',
            'name': 'Binance COIN-M',
            'urls': {
                'logo': 'https://github.com/user-attachments/assets/387cfc4e-5f33-48cd-8f5c-cd4854dabf0c',
                'doc': [
                    'https://binance-docs.github.io/apidocs/delivery/en/',
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
                    'types': [
                        'inverse',
                    ],
                },
                'defaultSubType': 'inverse',
                'leverageBrackets': undefined,
            },
        });
    }
    async transferIn(code, amount, params = {}) {
        // transfer from spot wallet to coinm futures wallet
        return await this.futuresTransfer(code, amount, 3, params);
    }
    async transferOut(code, amount, params = {}) {
        // transfer from coinm futures wallet to spot wallet
        return await this.futuresTransfer(code, amount, 4, params);
    }
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/binancecoinm.js`.

**Classes defined**: binancecoinm

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 46
- Code lines: 41
- Comment lines: 4
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./binance.js` (imported)
- `./binance.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/binancecoinm.js
```

