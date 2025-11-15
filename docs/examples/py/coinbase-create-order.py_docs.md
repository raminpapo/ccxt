# Documentation: examples/py/coinbase-create-order.py

## File Metadata

- **Path**: `examples/py/coinbase-create-order.py`
- **Size**: 977 bytes
- **Lines**: 40
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

# -----------------------------------------------------------------------------

print('CCXT Version:', ccxt.__version__)

# -----------------------------------------------------------------------------

exchange = ccxt.coinbase({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_API_SECRET',
    # 'verbose': True,  # for debug output
})

symbol = 'BTC/USDT'
order_type = 'limit'
side = 'buy'
amount = 0.0003
order_price = 13500
stop_params = {
    'triggerPrice': 15000
}

try:
    limit_order = exchange.create_order(symbol, order_type, side, amount, order_price)
    # stop_order = exchange.create_order(symbol, order_type, side, amount, order_price, stop_params)
    pprint(limit_order)
    # pprint(stop_order)
except Exception as err:
    print(err)

```

## High-Level Overview

This is a Python file located at `examples/py/coinbase-create-order.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 40
- Code lines: 24
- Comment lines: 6
- Blank lines: 10

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
python examples/py/coinbase-create-order.py
```

