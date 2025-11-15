# Documentation: js/src/pro/binancecoinm.js

## File Metadata

- **Path**: `js/src/pro/binancecoinm.js`
- **Size**: 1,080 bytes
- **Lines**: 27
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
//  ---------------------------------------------------------------------------
import binance from './binance.js';
import binancecoinmRest from '../binancecoinm.js';
// ---------------------------------------------------------------------------
export default class binancecoinm extends binance {
    describe() {
        // eslint-disable-next-line new-cap
        const restInstance = new binancecoinmRest();
        const restDescribe = restInstance.describe();
        const extended = this.deepExtend(super.describe(), restDescribe);
        return this.deepExtend(extended, {
            'id': 'binancecoinm',
            'name': 'Binance COIN-M',
            'urls': {
                'logo': 'https://user-images.githubusercontent.com/1294454/117738721-668c8d80-b205-11eb-8c49-3fad84c4a07f.jpg',
                'doc': 'https://developers.binance.com/en',
            },
            'options': {
                'fetchMarkets': {
                    'types': ['inverse'],
                },
                'defaultSubType': 'inverse',
            },
        });
    }
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/pro/binancecoinm.js`.

**Classes defined**: binancecoinm

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 23
- Comment lines: 3
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./binance.js` (imported)
- `../binancecoinm.js` (imported)
- `./binance.js` (referenced)
- `https://user-images.githubusercontent.com/1294454/117738721-668c8d80-b205-11eb-8c49-3fad84c4a07f.jpg` (referenced)
- `../binancecoinm.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/pro/binancecoinm.js
```

