# Documentation: wiki/examples/py/binance-fetch-all-my-trades.md

## File Metadata

- **Path**: `wiki/examples/py/binance-fetch-all-my-trades.md`
- **Size**: 1,219 bytes
- **Lines**: 55
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Binance Fetch All My Trades](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/binance-fetch-all-my-trades.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 55
- Code lines: 33
- Comment lines: 5
- Blank lines: 17

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

