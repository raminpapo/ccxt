# Documentation: examples/js/watchPositions-many-exchanges-continuosly.js

## File Metadata

- **Path**: `examples/js/watchPositions-many-exchanges-continuosly.js`
- **Size**: 1,429 bytes
- **Lines**: 50
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import ccxt from '../../js/ccxt.js';
// AUTO-TRANSPILE //
// watch and handle constinuosly
async function watchPositionsContinuously(exchange) {
    while (true) {
        try {
            const positions = await exchange.watchPositions();
            console.log('Fetched ', exchange.id, ' - Positions: ', positions);
        }
        catch (e) {
            console.log(e);
            break;
        }
    }
}
// start exchanges and fetch OHLCV loop
async function startExchange(exchangeName, config) {
    const ex = new ccxt[exchangeName](config);
    const promises = [];
    promises.push(watchPositionsContinuously(ex));
    await Promise.all(promises);
    await ex.close();
}
// main function
async function example() {
    const exchanges = {
        'binanceusdm': {
            'apiKey': 'YOUR_API_KEY',
            'secret': 'YOUR_API_SECRET',
        },
        'okx': {
            'apiKey': 'YOUR_API_KEY',
            'secret': 'YOUR_API_SECRET',
        },
        'huobi': {
            'apiKey': 'YOUR_API_KEY',
            'secret': 'YOUR_API_SECRET',
        },
    };
    const promises = [];
    const exchangeIds = Object.keys(exchanges);
    for (let i = 0; i < exchangeIds.length; i++) {
        const exchangeName = exchangeIds[i];
        const config = exchanges[exchangeName];
        promises.push(startExchange(exchangeName, config));
    }
    await Promise.all(promises);
}
await example();

```

## High-Level Overview

This is a JavaScript file located at `examples/js/watchPositions-many-exchanges-continuosly.js`.

**Functions defined**: async, example, watchPositionsContinuously, startExchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 50
- Code lines: 45
- Comment lines: 4
- Blank lines: 1

### Main Components

**Functions** (4):
- `async()`
- `example()`
- `startExchange()`
- `watchPositionsContinuously()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

- `../../js/ccxt.js` (imported)
- `../../js/ccxt.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node examples/js/watchPositions-many-exchanges-continuosly.js
```

