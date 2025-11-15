# Documentation: examples/py/order-book-extra-level-depth-param.py

## File Metadata

- **Path**: `examples/py/order-book-extra-level-depth-param.py`
- **Size**: 321 bytes
- **Lines**: 14
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

# return up to ten bidasks on each side of the order book stack
limit = 10
print(ccxt.cex().fetch_order_book('BTC/USD', limit))

```

## High-Level Overview

This is a Python file located at `examples/py/order-book-extra-level-depth-param.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 14
- Code lines: 7
- Comment lines: 2
- Blank lines: 5

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
python examples/py/order-book-extra-level-depth-param.py
```

