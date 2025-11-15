# Documentation: wiki/examples/py/poloniex-fetch-order-books.md

## File Metadata

- **Path**: `wiki/examples/py/poloniex-fetch-order-books.md`
- **Size**: 738 bytes
- **Lines**: 36
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Poloniex Fetch Order Books](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/poloniex-fetch-order-books.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 17
- Comment lines: 7
- Blank lines: 12

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

