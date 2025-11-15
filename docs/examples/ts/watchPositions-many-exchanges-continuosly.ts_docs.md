# Documentation: examples/ts/watchPositions-many-exchanges-continuosly.ts

## File Metadata

- **Path**: `examples/ts/watchPositions-many-exchanges-continuosly.ts`
- **Size**: 1,441 bytes
- **Lines**: 54
- **Type**: TypeScript
- **Extension**: .ts


## Original Source Code

```typescript
import ccxt from '../../js/ccxt.js';

// AUTO-TRANSPILE //

// watch and handle constinuosly
async function watchPositionsContinuously (exchange) {
    while (true) {
        try {
            const positions = await exchange.watchPositions ();
            console.log ('Fetched ', exchange.id, ' - Positions: ', positions);
        } catch (e) {
            console.log (e);
            break;
        }
    }
}

// start exchanges and fetch OHLCV loop
async function startExchange (exchangeName, config) {
    const ex = new ccxt[exchangeName] (config);
    const promises = [];
    promises.push (watchPositionsContinuously (ex));
    await Promise.all (promises);
    await ex.close ();
}

// main function
async function example () {
    const exchanges = {
        'binanceusdm': {
            'apiKey': 'YOUR_API_KEY',
            'secret': 'YOUR_API_SECRET',
        },
        'okx': {
            'apiKey': 'YOUR_API_KEY',
            'secret': 'YOUR_API_SECRET',
        },
        'huobi':{
            'apiKey': 'YOUR_API_KEY',
            'secret': 'YOUR_API_SECRET',
        },
    };
    const promises = [];
    const exchangeIds = Object.keys (exchanges);
    for (let i = 0; i < exchangeIds.length; i++) {
        const exchangeName = exchangeIds[i];
        const config = exchanges[exchangeName];
        promises.push (startExchange (exchangeName, config));
    }
    await Promise.all (promises);
}

await example ();

```

## High-Level Overview

This is a TypeScript file located at `examples/ts/watchPositions-many-exchanges-continuosly.ts`.

**Functions defined**: async, example, watchPositionsContinuously, startExchange

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 54
- Code lines: 44
- Comment lines: 4
- Blank lines: 6

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

**To execute this TypeScript file:**

```bash
ts-node examples/ts/watchPositions-many-exchanges-continuosly.ts
```

