# Documentation: examples/py/latoken-create-order.py

## File Metadata

- **Path**: `examples/py/latoken-create-order.py`
- **Size**: 487 bytes
- **Lines**: 26
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt  # noqa: E402


exchange = ccxt.latoken({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})

symbol = 'ETH/BTC'
type = 'limit'  # only support limit
side = 'buy'  # or 'sell'
amount = 0.01
price = 0.015881  # or None

order = exchange.create_order(symbol, type, side, amount, price)

print(order)

```

## High-Level Overview

This is a Python file located at `examples/py/latoken-create-order.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 16
- Comment lines: 1
- Blank lines: 9

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
python examples/py/latoken-create-order.py
```

