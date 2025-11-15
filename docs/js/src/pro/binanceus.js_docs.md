# Documentation: js/src/pro/binanceus.js

## File Metadata

- **Path**: `js/src/pro/binanceus.js`
- **Size**: 2,886 bytes
- **Lines**: 66
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
//  ---------------------------------------------------------------------------
import binance from './binance.js';
import binanceusRest from '../binanceus.js';
// ---------------------------------------------------------------------------
export default class binanceus extends binance {
    describe() {
        // eslint-disable-next-line new-cap
        const restInstance = new binanceusRest();
        const restDescribe = restInstance.describe();
        const parentWsDescribe = super.describeData();
        const extended = this.deepExtend(restDescribe, parentWsDescribe);
        return this.deepExtend(extended, {
            'id': 'binanceus',
            'name': 'Binance US',
            'countries': ['US'],
            'certified': false,
            'urls': {
                'logo': 'https://user-images.githubusercontent.com/1294454/65177307-217b7c80-da5f-11e9-876e-0b748ba0a358.jpg',
                'api': {
                    'ws': {
                        'spot': 'wss://stream.binance.us:9443/ws',
                    },
                    'web': 'https://www.binance.us',
                    'sapi': 'https://api.binance.us/sapi/v1',
                    'wapi': 'https://api.binance.us/wapi/v3',
                    'public': 'https://api.binance.us/api/v3',
                    'private': 'https://api.binance.us/api/v3',
                    'v3': 'https://api.binance.us/api/v3',
                    'v1': 'https://api.binance.us/api/v1',
                },
                'www': 'https://www.binance.us',
                'referral': 'https://www.binance.us/?ref=35005074',
                'doc': 'https://github.com/binance-us/binance-official-api-docs',
                'fees': 'https://www.binance.us/en/fee/schedule',
            },
            'has': {
                'createOrderWithTakeProfitAndStopLossWs': false,
                'createReduceOnlyOrderWs': false,
                'createStopLossOrderWs': false,
                'createTakeProfitOrderWs': false,
                'fetchPositionForSymbolWs': false,
                'fetchPositionsForSymbolWs': false,
                'fetchPositionsWs': false,
                'fetchPositionWs': false,
                'unWatchPositions': false,
                'watchLiquidations': false,
                'watchLiquidationsForSymbols': false,
                'watchMarkPrice': false,
                'watchMarkPrices': false,
                'watchMyLiquidations': false,
                'watchMyLiquidationsForSymbols': false,
                'watchPosition': false,
                'watchPositions': false,
            },
            'options': {
                'fetchCurrencies': false,
                'quoteOrderQty': false,
                'defaultType': 'spot',
                'fetchMarkets': {
                    'types': ['spot'],
                },
            },
        });
    }
}

```

## High-Level Overview

This is a JavaScript file located at `js/src/pro/binanceus.js`.

**Classes defined**: binanceus

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 66
- Code lines: 62
- Comment lines: 3
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./binance.js` (imported)
- `../binanceus.js` (imported)
- `./binance.js` (referenced)
- `https://user-images.githubusercontent.com/1294454/65177307-217b7c80-da5f-11e9-876e-0b748ba0a358.jpg` (referenced)
- `https://www.binance.us` (referenced)
- `../binanceus.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/pro/binanceus.js
```

