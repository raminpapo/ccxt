# Documentation: examples/py/binance-market-order-quote-usdt.py

## File Metadata

- **Path**: `examples/py/binance-market-order-quote-usdt.py`
- **Size**: 1,299 bytes
- **Lines**: 55
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

## High-Level Overview

This is a Python file located at `examples/py/binance-market-order-quote-usdt.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 55
- Code lines: 29
- Comment lines: 7
- Blank lines: 19

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
python examples/py/binance-market-order-quote-usdt.py
```

