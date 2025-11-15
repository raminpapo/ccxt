# Documentation: examples/py/coinbase-fetch-trades.py

## File Metadata

- **Path**: `examples/py/coinbase-fetch-trades.py`
- **Size**: 834 bytes
- **Lines**: 35
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
    # 'verbose': True,  # for debug output
})

symbol = 'BTC/USDT'
since = None  # not used by coinbase
limit = 3

try:
    trades = exchange.fetch_trades(symbol, since, limit)
    my_trades = exchange.fetch_my_trades(symbol, since, limit)
    pprint(trades)
    pprint(my_trades)
except Exception as err:
    print(err)

```

## High-Level Overview

This is a Python file located at `examples/py/coinbase-fetch-trades.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 21
- Comment lines: 4
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
python examples/py/coinbase-fetch-trades.py
```

