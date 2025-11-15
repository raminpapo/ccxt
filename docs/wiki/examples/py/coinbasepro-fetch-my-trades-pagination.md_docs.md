# Documentation: wiki/examples/py/coinbasepro-fetch-my-trades-pagination.md

## File Metadata

- **Path**: `wiki/examples/py/coinbasepro-fetch-my-trades-pagination.md`
- **Size**: 950 bytes
- **Lines**: 46
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Coinbasepro Fetch My Trades Pagination](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys

import ccxt  # noqa: E402

'''
Example snippet to traverse CoinBase Pro pagination.
Useful for reaching back more than 100 myTrades, the same works
for fetchClosedOrders
'''

exchange = ccxt.coinbasepro({
    "apiKey": "123456",
    "secret": "/abcdefghijklmnop/w==",
    "password": "987654321",
    "enableRateLimit": True
})

param_key = ''
param_value = ''
allMyTrades = []

while True:
    myTrades = exchange.fetch_my_trades(symbol='BTC/USD', params={param_key: param_value})

    # Handle with pagination ...
    if exchange.last_response_headers._store.get('cb-after'):
        param_key = 'after'
        param_value = exchange.last_response_headers._store['cb-after'][1]

        allMyTrades.extend(myTrades)

    else:
        allMyTrades.extend(myTrades)
        break

for trade in allMyTrades:
    print(trade)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/coinbasepro-fetch-my-trades-pagination.md`.

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 46
- Code lines: 31
- Comment lines: 4
- Blank lines: 11

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

