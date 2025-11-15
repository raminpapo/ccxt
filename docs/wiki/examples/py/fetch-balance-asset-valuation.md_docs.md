# Documentation: wiki/examples/py/fetch-balance-asset-valuation.md

## File Metadata

- **Path**: `wiki/examples/py/fetch-balance-asset-valuation.md`
- **Size**: 876 bytes
- **Lines**: 39
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Fetch Balance Asset Valuation](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/fetch-balance-asset-valuation.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 24
- Comment lines: 2
- Blank lines: 13

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

