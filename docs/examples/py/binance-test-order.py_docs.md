# Documentation: examples/py/binance-test-order.py

## File Metadata

- **Path**: `examples/py/binance-test-order.py`
- **Size**: 609 bytes
- **Lines**: 31
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


exchange = ccxt.binance({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})

symbol = 'ETH/BTC'
type = 'limit'  # or 'market'
side = 'sell'  # or 'buy'
amount = 1.0
price = 0.060154  # or None

# extra params and overrides if needed
params = {
    'test': True,  # test if it's valid, but don't actually place it
}

order = exchange.create_order(symbol, type, side, amount, price, params)

print(order)

```

## High-Level Overview

This is a Python file located at `examples/py/binance-test-order.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 19
- Comment lines: 2
- Blank lines: 10

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
pytest examples/py/binance-test-order.py
```

