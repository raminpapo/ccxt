# Documentation: wiki/examples/py/gateio-futures.md

## File Metadata

- **Path**: `wiki/examples/py/gateio-futures.md`
- **Size**: 1,148 bytes
- **Lines**: 55
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Gateio Futures](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
from random import randint
import sys


import ccxt  # noqa: E402


print('CCXT Version:', ccxt.__version__)

exchange = ccxt.gateio({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET_KEY',
    'options': {
        'defaultType': 'future',
    },
})

markets = exchange.load_markets()

# exchange.verbose = True  # uncomment for debugging purposes if necessary

# Example 1: Creating a future (market) order
try:
    # find a valid future
    futures = []
    for key in markets:
        market = markets[key]
        if market['future']:
            futures.append(market)
    
    if len(futures) > 0:
        market = futures[0]
        symbol = market['symbol'] # example: BTC/USDT:USDT-220318
        type = 'market'
        side = 'buy'
        amount = 1

        # placing an order
        order = exchange.create_order(symbol, type, side, amount)
        print(order)

        # listing open orders
        open_orders = exchange.fetch_open_orders(symbol)
        print(open_orders)

except Exception as e:
    print(type(e).__name__, str(e)) 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/gateio-futures.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 55
- Code lines: 34
- Comment lines: 6
- Blank lines: 15

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

