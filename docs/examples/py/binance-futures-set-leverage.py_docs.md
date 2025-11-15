# Documentation: examples/py/binance-futures-set-leverage.py

## File Metadata

- **Path**: `examples/py/binance-futures-set-leverage.py`
- **Size**: 378 bytes
- **Lines**: 22
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


exchange = ccxt.binanceusdm({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})

exchange.load_markets()

response = exchange.set_leverage(10, 'ADA/USDT')

print(response)

```

## High-Level Overview

This is a Python file located at `examples/py/binance-futures-set-leverage.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 12
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
python examples/py/binance-futures-set-leverage.py
```

