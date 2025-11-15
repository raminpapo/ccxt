# Documentation: wiki/examples/py/fetch-open-orders.md

## File Metadata

- **Path**: `wiki/examples/py/fetch-open-orders.md`
- **Size**: 986 bytes
- **Lines**: 41
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Fetch Open Orders](./examples/py/)


 ```python
 import ccxt
from pprint import pprint


print('CCXT Version:', ccxt.__version__)


exchange = ccxt.binance({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})


markets = exchange.load_markets()
# exchange.verbose = True  # uncomment for debugging purposes if necessary

symbol = 'BTC/USDT'  # says itself

# the since argument must be an integer in milliseconds throughout the lib
since = exchange.parse8601('2021-06-20T00:00:00')  # parse it from ISO8601 datetime string

# how many orders to return, max integer or None to use the exchanges' defaults
limit = None

# your params-overrides here if necessary
params = {
    # https://github.com/ccxt/ccxt/wiki/Manual#overriding-unified-api-params
}

try:
    # https://github.com/ccxt/ccxt/wiki/Manual#querying-orders
    orders = exchange.fetch_open_orders(symbol, since, limit, params)
    pprint(orders)
except Exception as e:
    print(type(e).__name__, str(e))
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/fetch-open-orders.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 21
- Comment lines: 6
- Blank lines: 14

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

