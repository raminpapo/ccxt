# Documentation: wiki/examples/py/coinbase-fetch-ticker.md

## File Metadata

- **Path**: `wiki/examples/py/coinbase-fetch-ticker.md`
- **Size**: 744 bytes
- **Lines**: 33
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Coinbase Fetch Ticker](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint


import ccxt  # noqa: E402
print('CCXT Version:', ccxt.__version__)
exchange = ccxt.coinbase({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_API_SECRET',
    # some markets are not supported with v2 like BTC/USDT
    'options': {'fetchTicker': 'fetchTickerV3', 'fetchTickers': 'fetchTickersV3'}  # for selecting previous versions
    # 'verbose': True,  # for debug output
})

symbols = ['BTC/USDT', 'ETH/USDT']
symbol = 'BTC/USDT'

try:
    tickers = exchange.fetch_tickers(symbols)
    ticker = exchange.fetch_ticker(symbol)
    pprint(tickers)
    pprint(ticker)
except Exception as err:
    print(err)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/coinbase-fetch-ticker.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 22
- Comment lines: 3
- Blank lines: 8

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

