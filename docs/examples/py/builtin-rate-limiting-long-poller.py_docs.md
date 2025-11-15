# Documentation: examples/py/builtin-rate-limiting-long-poller.py

## File Metadata

- **Path**: `examples/py/builtin-rate-limiting-long-poller.py`
- **Size**: 348 bytes
- **Lines**: 17
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


exchange = ccxt.bitfinex()

for i in range(0, 10):
    # this can be any call instead of fetch_ticker, really
    print(exchange.fetch_ticker('BTC/USD'))

```

## High-Level Overview

This is a Python file located at `examples/py/builtin-rate-limiting-long-poller.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 8
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
python examples/py/builtin-rate-limiting-long-poller.py
```

