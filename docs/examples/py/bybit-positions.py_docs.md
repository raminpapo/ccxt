# Documentation: examples/py/bybit-positions.py

## File Metadata

- **Path**: `examples/py/bybit-positions.py`
- **Size**: 1,155 bytes
- **Lines**: 39
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

from pprint import pprint

print('CCXT Version:', ccxt.__version__)

exchange = ccxt.bybit ({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})

markets = exchange.load_markets() # https://github.com/ccxt/ccxt/wiki/Manual#loading-markets

exchange.verbose = True  # uncomment for debugging

# -----------------------------------------------------------------------------

symbol = 'BTC/USDT:USDT'  # https://github.com/ccxt/ccxt/wiki/Manual#contract-naming-conventions
market = exchange.market(symbol)
params = {'subType':'linear' if market['linear'] else 'inverse'}
linear_positions = exchange.fetch_positions([ symbol ], params)
pprint(linear_positions)

# -----------------------------------------------------------------------------

symbol = 'BTC/USD:BTC'
market = exchange.market(symbol)
params = {'subType':'linear' if market['linear'] else 'inverse'}
inverse_positions = exchange.fetch_positions([ symbol ], params)
pprint(inverse_positions)

```

## High-Level Overview

This is a Python file located at `examples/py/bybit-positions.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 23
- Comment lines: 3
- Blank lines: 13

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
python examples/py/bybit-positions.py
```

