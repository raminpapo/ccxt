# Documentation: examples/py/krakenfutures-basic.py

## File Metadata

- **Path**: `examples/py/krakenfutures-basic.py`
- **Size**: 680 bytes
- **Lines**: 25
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt  # noqa: E402

print("CCXT Version:", ccxt.__version__)


exchange = ccxt.krakenfutures()
markets = exchange.load_markets()
# exchange.verbose = True  # uncomment for debugging purposes if necessary
print(exchange.name, "supports the following methods:")
pprint(exchange.has)
print(exchange.name, "supports the following trading symbols:")
for symbol in exchange.symbols:
    print(symbol)
symbol = 'BTC/USD:USD'
orderbook = exchange.fetch_order_book(symbol)
pprint(orderbook)
```

## High-Level Overview

This is a Python file located at `examples/py/krakenfutures-basic.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 17
- Comment lines: 2
- Blank lines: 6

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
python examples/py/krakenfutures-basic.py
```

