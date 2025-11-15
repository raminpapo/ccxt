# Documentation: wiki/examples/js/binance-fetchTicker-delivery-vs-future.md

## File Metadata

- **Path**: `wiki/examples/js/binance-fetchTicker-delivery-vs-future.md`
- **Size**: 842 bytes
- **Lines**: 36
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Binance Fetchticker Delivery Vs Future](./examples/js/)


 ```javascript
 

import ccxt from '../../js/ccxt.js';

async function fetchTickers (exchange) {
    let tickers = undefined
    try {
        // await exchange.loadMarkets () // optional
        tickers = await exchange.fetchTickers ()
    } catch (e) {
        console.error (e.constructor.name, e.message)
    }
    return tickers
}

(async () => {

    const future   = new ccxt.binance ({ options: { defaultType: 'future' }})
    const delivery = new ccxt.binance ({ options: { defaultType: 'delivery' }})

    // ...

    const futureTickers = await fetchTickers (future);
    console.log (futureTickers)

    console.log ('-------------------------------------------')

    const deliveryTickers = await fetchTickers (delivery);
    console.log (deliveryTickers)

}) () 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/js/binance-fetchTicker-delivery-vs-future.md`.

**Functions defined**: fetchTickers

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 22
- Comment lines: 2
- Blank lines: 12

### Main Components

**Functions** (1):
- `fetchTickers()`



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

