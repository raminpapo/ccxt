# Documentation: examples/py/bybit-USDC-create-option-order.py

## File Metadata

- **Path**: `examples/py/bybit-USDC-create-option-order.py`
- **Size**: 869 bytes
- **Lines**: 35
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

exchange = ccxt.bybit ({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_API_SECRET',
    'defaultType': 'option',
    # 'verbose': True,  # for debug output
})

# BASE/QUOTE:SETTLE-YYMMDD-STRIKE-C (end with C for call, end with P for put)
symbol = 'BTC/USD:USDC-221209-18000-C'
amount = 0.01
price = 280.0

try:
    order = exchange.create_order(symbol, 'limit', 'buy', amount, price)
    pprint(order)
except Exception as err:
    print(err)

```

## High-Level Overview

This is a Python file located at `examples/py/bybit-USDC-create-option-order.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 20
- Comment lines: 5
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
python examples/py/bybit-USDC-create-option-order.py
```

