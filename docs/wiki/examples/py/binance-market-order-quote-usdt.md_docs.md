# Documentation: wiki/examples/py/binance-market-order-quote-usdt.md

## File Metadata

- **Path**: `wiki/examples/py/binance-market-order-quote-usdt.md`
- **Size**: 1,252 bytes
- **Lines**: 58
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Binance Market Order Quote Usdt](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint


import ccxt  # noqa: E402


print('CCXT Version:', ccxt.__version__)


exchange = ccxt.binance({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})

markets = exchange.load_markets()

# exchange.verbose = True  # uncomment for debugging purposes if necessary

symbol = 'ETH/USDT'

try:

    print('--------------------------------------------------------------')

    # option 1 – specify price * amount
    amount = 1
    price = 4000
    # cost = amount * price
    # this line will use the amount * price to calculate the total cost-to-spend (4000)
    order = exchange.create_order(symbol, 'market', 'buy', amount, price)
    pprint(order)

    print('--------------------------------------------------------------')

    # option 2 – specify
    # this line does the same, but you override the cost via extra params
    params = {
        'quoteOrderQty': 4000,  # binance-specific
    }
    amount = None
    price = None
    order = exchange.create_order(symbol, 'market', 'buy', amount, price, params)
    pprint(order)

except Exception as e:
    print(type(e).__name__, str(e))


 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/binance-market-order-quote-usdt.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 58
- Code lines: 30
- Comment lines: 7
- Blank lines: 21

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

