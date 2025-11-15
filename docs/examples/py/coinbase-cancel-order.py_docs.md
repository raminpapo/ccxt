# Documentation: examples/py/coinbase-cancel-order.py

## File Metadata

- **Path**: `examples/py/coinbase-cancel-order.py`
- **Size**: 911 bytes
- **Lines**: 34
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

order_id = '04204eaf-94d6-444a-b9b7-2f8a485311f6'
# order_ids = ['04204eaf-94d6-444a-b9b7-2f8a485311f6', '7c13a059-d235-46e1-ab43-6794a5836db9']

try:
    cancel_order = exchange.cancel_order(order_id)
    # cancel_orders = exchange.cancel_orders(order_ids)
    pprint(cancel_order)
    # pprint(cancel_orders)
except Exception as err:
    print(err)

```

## High-Level Overview

This is a Python file located at `examples/py/coinbase-cancel-order.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 17
- Comment lines: 7
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
python examples/py/coinbase-cancel-order.py
```

