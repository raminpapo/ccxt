# Documentation: examples/py/binance-fetch-all-my-trades-paginate-by-id.py

## File Metadata

- **Path**: `examples/py/binance-fetch-all-my-trades-paginate-by-id.py`
- **Size**: 1,431 bytes
- **Lines**: 56
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

symbol = 'ETH/BTC'
from_id = '0'
params = { 'fromId': from_id }
previous_from_id = from_id

all_trades = []

while True:

    print('------------------------------------------------------------------')
    print('Fetching with params', params)
    trades = exchange.fetch_my_trades(symbol, None, None, params)
    print('Fetched', len(trades), 'trades')
    if len(trades):
        # for i in range(0, len(trades)):
        #     trade = trades[i]
        #     print (i, trade['id'], trade['datetime'], trade['amount'])
        last_trade = trades[len(trades) - 1]
        if last_trade['id'] == previous_from_id:
            break
        else:
            previous_from_id = last_trade['id']
            params['fromId'] = last_trade['id']
            all_trades = all_trades + trades
    else:
        break

print('Fetched', len(all_trades), 'trades')
for i in range(0, len(all_trades)):
    trade = all_trades[i]
    print (i, trade['id'], trade['datetime'], trade['amount'])

```

## High-Level Overview

This is a Python file located at `examples/py/binance-fetch-all-my-trades-paginate-by-id.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 56
- Code lines: 34
- Comment lines: 8
- Blank lines: 14

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
python examples/py/binance-fetch-all-my-trades-paginate-by-id.py
```

