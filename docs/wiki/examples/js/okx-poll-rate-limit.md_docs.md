# Documentation: wiki/examples/js/okx-poll-rate-limit.md

## File Metadata

- **Path**: `wiki/examples/js/okx-poll-rate-limit.md`
- **Size**: 1,156 bytes
- **Lines**: 54
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Okx Poll Rate Limit](./examples/js/)


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/okx-poll-rate-limit.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 54
- Code lines: 33
- Comment lines: 4
- Blank lines: 17

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

**To execute this Markdown file:**

