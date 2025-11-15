# Documentation: wiki/examples/py/krakenfutures-basic.md

## File Metadata

- **Path**: `wiki/examples/py/krakenfutures-basic.md`
- **Size**: 621 bytes
- **Lines**: 28
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Krakenfutures Basic](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/krakenfutures-basic.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 18
- Comment lines: 2
- Blank lines: 8

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

