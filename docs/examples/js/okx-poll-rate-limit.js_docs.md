# Documentation: examples/js/okx-poll-rate-limit.js

## File Metadata

- **Path**: `examples/js/okx-poll-rate-limit.js`
- **Size**: 1,093 bytes
- **Lines**: 49
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
import ccxt from '../../js/ccxt.js'

console.log ('CCXT Version:', ccxt.version)

async function main () {

    const exchange = new ccxt.okx ({

        // edit for your credentials
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_API_SECRET',
        'password': 'YOUR_API_PASSWORD',

        'api': {
            'private': {
                'get': {
                    'trade/fills-history': 2.2,
                },
            },
        },

    })

    await exchange.loadMarkets ()

    // if this script fails with a rate limiter error
    // uncomment the following line for debugging purposes

    // exchange.verbose = true

    const promises=[];
    for(let i=0;i<100;i++){
        promises.push(exchange.fetchMyTrades());
    }

    const allResponses = await Promise.allSettled(promises);
    allResponses.forEach((result, i) => {

        if(result.status == "fulfilled"){
            console.log (new Date(), i + 6, 'fetched', result.value.length, 'trades')
        } else {
            console.log ("Rejected:", i + 6, result.reason);
        }
    });

}

main ()

```

## High-Level Overview

This is a JavaScript file located at `examples/js/okx-poll-rate-limit.js`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 49
- Code lines: 30
- Comment lines: 4
- Blank lines: 15

### Main Components

**Functions** (1):
- `main()`



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
node examples/js/okx-poll-rate-limit.js
```

