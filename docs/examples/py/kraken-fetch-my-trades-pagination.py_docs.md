# Documentation: examples/py/kraken-fetch-my-trades-pagination.py

## File Metadata

- **Path**: `examples/py/kraken-fetch-my-trades-pagination.py`
- **Size**: 1,433 bytes
- **Lines**: 47
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


exchange = ccxt.kraken({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_API_SECRET',
})

exchange.load_markets()

# exchange.verbose = True  # uncomment for verbose debug output

exchange.rateLimit = 10000  # set a higher value if you get rate-limiting errors

all_trades = []
offset = 0
while True:
    trades = exchange.fetch_my_trades(symbol=None, since=None, limit=None, params={'ofs': offset})
    print('-----------------------------------------------------------------')
    print(exchange.iso8601(exchange.milliseconds()), 'Fetched', len(trades), 'trades')
    if len(trades) < 1:
        break
    else:
        first = exchange.safe_value(trades, 0)
        last = exchange.safe_value(trades, len(trades) - 1)
        print('From:', first['datetime'])
        print('To:', last['datetime'])
        all_trades = trades + all_trades
        offset += len(trades)
    print(len(all_trades), 'trades fetched in total')

print('-----------------------------------------------------------------')
print(len(all_trades), 'trades fetched')
first = exchange.safe_value(all_trades, 0)
if first:
    last = exchange.safe_value(all_trades, len(all_trades) - 1)
    print('First:', first['datetime'])
    print('Last:', last['datetime'])

```

## High-Level Overview

This is a Python file located at `examples/py/kraken-fetch-my-trades-pagination.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 34
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
python examples/py/kraken-fetch-my-trades-pagination.py
```

