# Documentation: examples/py/fetch-balance-asset-valuation.py

## File Metadata

- **Path**: `examples/py/fetch-balance-asset-valuation.py`
- **Size**: 925 bytes
- **Lines**: 36
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt  # noqa: E402


print('CCXT Version:', ccxt.__version__)


exchange = ccxt.binance({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})


markets = exchange.load_markets()
# exchange.verbose = True  # uncomment for debugging purposes if necessary
balance = exchange.fetch_balance()
tickers = exchange.fetch_tickers()
destination_code = 'USDT'
total_destination_value = 0
for code, amount in balance['total'].items():
    symbol = code + '/' + destination_code
    ticker = tickers.get(symbol, None)
    if ticker is not None:
        valuation = amount * ticker['last']
        total_destination_value += valuation
        print(amount, code, '=', valuation, destination_code)


print('Total', total_destination_value, destination_code)
```

## High-Level Overview

This is a Python file located at `examples/py/fetch-balance-asset-valuation.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 23
- Comment lines: 2
- Blank lines: 11

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
python examples/py/fetch-balance-asset-valuation.py
```

