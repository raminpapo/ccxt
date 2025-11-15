# Documentation: examples/py/gateio-open-close-contract.py

## File Metadata

- **Path**: `examples/py/gateio-open-close-contract.py`
- **Size**: 1,300 bytes
- **Lines**: 56
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
from random import randint
import sys
from pprint import pprint

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt  # noqa: E402


print('CCXT Version:', ccxt.__version__)

exchange = ccxt.gateio({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
    'options': {
        'defaultType': 'swap',
    },
})

# exchange.set_sandbox_mode(True) 

markets = exchange.load_markets()

exchange.verbose = True  # uncomment for debugging purposes if necessary


# Example: creating and closing a contract
symbol = 'LTC/USDT:USDT'
order_type = 'market'
side = 'buy'
amount = 1

try:
    # fetching current balance
    balance = exchange.fetch_balance()
    # print(balance)

    # placing an order/ opening contract position
    order = exchange.create_order(symbol, order_type, side, amount)
    # print(order)

    # closing it by issuing an oposite contract 
    # and therefore close our previous position
    side = 'sell'
    type = 'market'
    reduce_only = True
    params = {'reduce_only': reduce_only}
    opositeOrder = exchange.create_order(symbol, order_type, side, amount, None, params)
    print(opositeOrder)
except Exception as e:
    print(type(e).__name__, str(e))

```

## High-Level Overview

This is a Python file located at `examples/py/gateio-open-close-contract.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 56
- Code lines: 32
- Comment lines: 9
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
python examples/py/gateio-open-close-contract.py
```

