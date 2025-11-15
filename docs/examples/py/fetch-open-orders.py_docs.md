# Documentation: examples/py/fetch-open-orders.py

## File Metadata

- **Path**: `examples/py/fetch-open-orders.py`
- **Size**: 929 bytes
- **Lines**: 36
- **Type**: Python
- **Extension**: .py


## Original Source Code

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

## High-Level Overview

This is a Python file located at `examples/py/fetch-open-orders.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 18
- Comment lines: 6
- Blank lines: 12

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/fetch-open-orders.py
```

