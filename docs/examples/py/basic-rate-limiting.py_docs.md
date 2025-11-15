# Documentation: examples/py/basic-rate-limiting.py

## File Metadata

- **Path**: `examples/py/basic-rate-limiting.py`
- **Size**: 573 bytes
- **Lines**: 26
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

from pprint import pprint

import os
import sys

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt  # noqa: E402


symbol = 'ETH/BTC'

exchange = ccxt.poloniex({
    'enableRateLimit': True,  # enabled by default
})

# print 10 times with appropriate delay
for i in range(0, 10):
    print('--------------------------------------------------------------------')
    ticker = exchange.fetch_ticker(symbol)
    ticker = exchange.omit(ticker, 'info')
    pprint(ticker)

```

## High-Level Overview

This is a Python file located at `examples/py/basic-rate-limiting.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 15
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
python examples/py/basic-rate-limiting.py
```

