# Documentation: examples/py/phemex-create-stop-order.py

## File Metadata

- **Path**: `examples/py/phemex-create-stop-order.py`
- **Size**: 792 bytes
- **Lines**: 43
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

exchange = ccxt.phemex({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})

# exchange.set_sandbox_mode(True)

# Example 1: Creating stop-market order
symbol = 'LTC/USDT'
type = 'market'
side = 'buy'
amount = 0.5

params = {
    'stopPrice': 50,
}

stop_market = exchange.create_order(symbol, type, side, amount, None, params)
print(stop_market)

# Example 2: Create stop-limit order
symbol = 'LTC/USDT'
type = 'limit'
side = 'buy'
amount = 0.5
price = 70

params = {
    'stopPrice': 50,
}

stop_limit = exchange.create_order(symbol, type, side, amount, price, params)
print(stop_limit)
```

## High-Level Overview

This is a Python file located at `examples/py/phemex-create-stop-order.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 43
- Code lines: 28
- Comment lines: 4
- Blank lines: 11

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
python examples/py/phemex-create-stop-order.py
```

