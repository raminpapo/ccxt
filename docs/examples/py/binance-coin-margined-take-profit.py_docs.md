# Documentation: examples/py/binance-coin-margined-take-profit.py

## File Metadata

- **Path**: `examples/py/binance-coin-margined-take-profit.py`
- **Size**: 838 bytes
- **Lines**: 39
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

exchange = ccxt.binancecoinm({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})

markets = exchange.load_markets()

exchange.verbose = True  # uncomment for debugging purposes if necessary

# edit for your values below

symbol = 'EOS/USD'
order_type = 'TAKE_PROFIT'
side = 'sell'
amount = YOUR_AMOUNT_HERE
price = YOUR_LIMIT_PRICE_HERE
stopPrice = YOUR_STOP_PRICE
params = {'stopPrice': stopPrice}

try:
    order = exchange.create_order(symbol, order_type, side, amount, price, params)
    print(order)
except Exception as e:
    print(type(e).__name__, str(e))

```

## High-Level Overview

This is a Python file located at `examples/py/binance-coin-margined-take-profit.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 25
- Comment lines: 2
- Blank lines: 12

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
python examples/py/binance-coin-margined-take-profit.py
```

