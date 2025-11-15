# Documentation: examples/py/poloniex-fetch-order-books.py

## File Metadata

- **Path**: `examples/py/poloniex-fetch-order-books.py`
- **Size**: 790 bytes
- **Lines**: 33
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

id = 'poloniex'

# instantiate the exchange by id
exchange = getattr(ccxt, id)({
    # 'proxy':'https://cors-anywhere.herokuapp.com/',
})

# load all markets from the exchange
markets = exchange.load_markets()

# this will work (a limited number of symbols)
result = exchange.fetch_order_books(['ETH/BTC', 'LTC/BTC'])
pprint(result)

# this will also work (a limited number of symbols)
result = exchange.fetch_order_books(exchange.symbols[0:10])
pprint(result)

# this will not work (too many symbols)
result = exchange.fetch_order_books(exchange.symbols)
pprint(result)

```

## High-Level Overview

This is a Python file located at `examples/py/poloniex-fetch-order-books.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 16
- Comment lines: 7
- Blank lines: 10

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
python examples/py/poloniex-fetch-order-books.py
```

