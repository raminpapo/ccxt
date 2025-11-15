# Documentation: examples/py/binance-fetch-all-my-trades.py

## File Metadata

- **Path**: `examples/py/binance-fetch-all-my-trades.py`
- **Size**: 1,270 bytes
- **Lines**: 52
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


exchange = ccxt.binance({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
    # 'options': {
    #     'defaultType': 'spot', // spot, future, margin
    # },
})


exchange.load_markets ()

# exchange.verbose = True  # uncomment for debugging

symbol = 'BTC/USDT'
day = 24 * 60 * 60 * 1000
start_time = exchange.parse8601 ('2020-03-01T00:00:00')
now = exchange.milliseconds ()

all_trades = []

while start_time < now:

    print('------------------------------------------------------------------')
    print('Fetching trades from', exchange.iso8601(start_time))
    end_time = start_time + day

    trades = exchange.fetch_my_trades (symbol, start_time, None, {
        'endTime': end_time,
    })
    if len(trades):
        last_trade = trades[len(trades) - 1]
        start_time = last_trade['timestamp'] + 1
        all_trades = all_trades + trades
    else:
        start_time = end_time

print('Fetched', len(all_trades), 'trades')
for i in range(0, len(all_trades)):
    trade = all_trades[i]
    print (i, trade['id'], trade['datetime'], trade['amount'])

```

## High-Level Overview

This is a Python file located at `examples/py/binance-fetch-all-my-trades.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 52
- Code lines: 32
- Comment lines: 5
- Blank lines: 15

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
python examples/py/binance-fetch-all-my-trades.py
```

