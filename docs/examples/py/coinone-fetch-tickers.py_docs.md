# Documentation: examples/py/coinone-fetch-tickers.py

## File Metadata

- **Path**: `examples/py/coinone-fetch-tickers.py`
- **Size**: 566 bytes
- **Lines**: 28
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

exchange = ccxt.coinone({
    # 'verbose': True,  # uncomment for verbose output
})

# fetch all
tickers = exchange.fetch_tickers()
for symbol, ticker in tickers.items():
    print(ticker)

print("\n")

# fetch one by one
markets = exchange.load_markets()
for symbol in markets.keys():
    ticker = exchange.fetch_ticker(symbol)
    print(ticker)

```

## High-Level Overview

This is a Python file located at `examples/py/coinone-fetch-tickers.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 16
- Comment lines: 4
- Blank lines: 8

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
python examples/py/coinone-fetch-tickers.py
```

