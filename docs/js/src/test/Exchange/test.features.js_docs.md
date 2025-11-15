# Documentation: js/src/test/Exchange/test.features.js

## File Metadata

- **Path**: `js/src/test/Exchange/test.features.js`
- **Size**: 4,290 bytes
- **Lines**: 125
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import testSharedMethods from './base/test.sharedMethods.js';
async function testFeatures(exchange, skippedProperties) {
    const marketTypes = ['spot', 'swap', 'future', 'option'];
    const subTypes = ['linear', 'inverse'];
    const features = exchange.features;
    const keys = Object.keys(features);
    for (let i = 0; i < keys.length; i++) {
        testSharedMethods.assertInArray(exchange, skippedProperties, 'features', keys, i, marketTypes);
        const marketType = keys[i];
        const value = features[marketType];
        // assert (value !== undefined, 'exchange.features["' + marketType + '"] is undefined, that key should be either absent or have a value');
        if (value === undefined) {
            continue;
        }
        if (marketType === 'spot') {
            testFeaturesInner(exchange, skippedProperties, value);
        }
        else {
            const subKeys = Object.keys(value);
            for (let j = 0; j < subKeys.length; j++) {
                const subKey = subKeys[j];
                testSharedMethods.assertInArray(exchange, skippedProperties, 'features', subKeys, j, subTypes);
                const subValue = value[subKey];
                // sometimes it might not be available for exchange, eg. future>inverse)
                if (subValue !== undefined) {
                    testFeaturesInner(exchange, skippedProperties, subValue);
                }
            }
        }
    }
    return true;
}
function testFeaturesInner(exchange, skippedProperties, featureObj) {
    const format = {
        'sandbox': false,
        'createOrder': {
            'marginMode': false,
            'triggerPrice': false,
            'triggerPriceType': {
                'mark': false,
                'last': false,
                'index': false,
            },
            'stopLossPrice': false,
            'takeProfitPrice': false,
            'attachedStopLossTakeProfit': {
                'triggerPriceType': {
                    'last': false,
                    'mark': false,
                    'index': false,
                },
                'price': false,
            },
            'timeInForce': {
                'GTC': false,
                'IOC': false,
                'FOK': false,
                'PO': false,
                'GTD': false,
                // 'GTX': false,
            },
            'hedged': false,
            // exchange-supported features
            'trailing': false,
            // 'iceberg': false,
            // 'twap': false,
            // 'selfTradePrevention': false,
            // 'oco': false,
        },
        'createOrders': {
            'max': 5,
        },
        'fetchMyTrades': {
            'marginMode': false,
            'daysBack': 0,
            'limit': 0,
            'untilDays': 0,
            'symbolRequired': false,
        },
        'fetchOrder': {
            'marginMode': false,
            'trigger': false,
            'trailing': false,
            'symbolRequired': false,
        },
        'fetchOpenOrders': {
            'marginMode': false,
            'limit': 0,
            'trigger': false,
            'trailing': false,
            'symbolRequired': false,
        },
        'fetchOrders': {
            'marginMode': false,
            'limit': 0,
            'daysBack': 0,
            'untilDays': 0,
            'trigger': false,
            'trailing': false,
            'symbolRequired': false,
        },
        'fetchClosedOrders': {
            'marginMode': false,
            'limit': 0,
            'daysBack': 0,
            'daysBackCanceled': 0,
            'untilDays': 0,
            'trigger': false,
            'trailing': false,
            'symbolRequired': false,
        },
        'fetchOHLCV': {
            'limit': 0,
        },
    };
    const featureKeys = Object.keys(featureObj);
    const allMethods = Object.keys(exchange.has);
    for (let i = 0; i < featureKeys.length; i++) {
        testSharedMethods.assertInArray(exchange, skippedProperties, 'features', featureKeys, i, allMethods);
        testSharedMethods.assertStructure(exchange, skippedProperties, 'features', featureObj, format, undefined, true); // deep structure check
    }
    // return true;
}
export default testFeatures;

```

## High-Level Overview

This is a JavaScript file located at `js/src/test/Exchange/test.features.js`.

**Functions defined**: testFeaturesInner, testFeatures

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 125
- Code lines: 115
- Comment lines: 9
- Blank lines: 1

### Main Components

**Functions** (2):
- `testFeatures()`
- `testFeaturesInner()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `./base/test.sharedMethods.js` (imported)
- `./base/test.sharedMethods.js` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
npm test js/src/test/Exchange/test.features.js
```

