# Documentation: examples/py/coinbase-fetch-ticker.py

## File Metadata

- **Path**: `examples/py/coinbase-fetch-ticker.py`
- **Size**: 965 bytes
- **Lines**: 36
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt  # noqa: E402

# -----------------------------------------------------------------------------

print('CCXT Version:', ccxt.__version__)

# -----------------------------------------------------------------------------

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

## High-Level Overview

This is a Python file located at `examples/py/coinbase-fetch-ticker.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 21
- Comment lines: 5
- Blank lines: 10

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
python examples/py/coinbase-fetch-ticker.py
```

