# Documentation: examples/py/fetch-okex-futures.py

## File Metadata

- **Path**: `examples/py/fetch-okex-futures.py`
- **Size**: 761 bytes
- **Lines**: 26
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys
import time

# ------------------------------------------------------------------------------

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

# ------------------------------------------------------------------------------

import ccxt  # noqa: E402

# ------------------------------------------------------------------------------

exchange = ccxt.okex()
exchange.load_markets()
for symbol in exchange.markets:
    market = exchange.markets[symbol]
    if market['future']:
        print('----------------------------------------------------')
        print(symbol, exchange.fetchTicker(symbol))
        time.sleep(exchange.rateLimit / 1000)

```

## High-Level Overview

This is a Python file located at `examples/py/fetch-okex-futures.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 14
- Comment lines: 4
- Blank lines: 8

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
python examples/py/fetch-okex-futures.py
```

