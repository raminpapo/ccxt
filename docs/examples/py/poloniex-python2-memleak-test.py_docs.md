# Documentation: examples/py/poloniex-python2-memleak-test.py

## File Metadata

- **Path**: `examples/py/poloniex-python2-memleak-test.py`
- **Size**: 734 bytes
- **Lines**: 27
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys
import psutil


# -----------------------------------------------------------------------------

this_folder = os.path.dirname(os.path.abspath(__file__))
root_folder = os.path.dirname(os.path.dirname(this_folder))
sys.path.append(root_folder + '/python')
sys.path.append(this_folder)

# -----------------------------------------------------------------------------

import ccxt  # noqa: E402

# -----------------------------------------------------------------------------

exchange = ccxt.poloniex()

while True:
    orderbook = exchange.fetch_order_book('ETH/BTC')
    process = psutil.Process(os.getpid())
    print(exchange.iso8601(exchange.milliseconds()), process.memory_info()[0])

```

## High-Level Overview

This is a Python file located at `examples/py/poloniex-python2-memleak-test.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 13
- Comment lines: 4
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
pytest examples/py/poloniex-python2-memleak-test.py
```

