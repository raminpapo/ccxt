# Documentation: examples/py/instantiate-all-at-once.py

## File Metadata

- **Path**: `examples/py/instantiate-all-at-once.py`
- **Size**: 447 bytes
- **Lines**: 19
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

exchanges = {}  # a placeholder for your instances

for id in ccxt.exchanges:
    exchange = getattr(ccxt, id)
    exchanges[id] = exchange()

# now exchanges dictionary contains all exchange instances...
exchanges['bittrex'].fetch_order_book('ETH/BTC')

```

## High-Level Overview

This is a Python file located at `examples/py/instantiate-all-at-once.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 10
- Comment lines: 2
- Blank lines: 7

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
python examples/py/instantiate-all-at-once.py
```

