# Documentation: examples/py/bitmex-create-order.py

## File Metadata

- **Path**: `examples/py/bitmex-create-order.py`
- **Size**: 699 bytes
- **Lines**: 30
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


exchange = ccxt.bitmex({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})

symbol = 'BTC/USD:BTC-220624'  # bitcoin contract according to https://github.com/ccxt/ccxt/wiki/Manual#symbols-and-market-ids
type = 'StopLimit'  # or 'Market', or 'Stop' or 'StopLimit'
side = 'sell'  # or 'buy'
amount = 1.0
price = 6500.0  # or None

# extra params and overrides
params = {
    'stopPx': 6000.0,  # if needed
}

order = exchange.create_order(symbol, type, side, amount, price, params)
print(order)

```

## High-Level Overview

This is a Python file located at `examples/py/bitmex-create-order.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 30
- Code lines: 19
- Comment lines: 2
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
python examples/py/bitmex-create-order.py
```

