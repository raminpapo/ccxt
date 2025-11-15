# Documentation: wiki/examples/py/bybit-conditional-orders.md

## File Metadata

- **Path**: `wiki/examples/py/bybit-conditional-orders.md`
- **Size**: 489 bytes
- **Lines**: 28
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Bybit Conditional Orders](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint


import ccxt  # noqa: E402

exchange = ccxt.bybit({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})

markets = exchange.load_markets()

# exchange.verbose = True  # uncomment for debugging purposes

params = {'stop_px': 9750, 'base_price':11152}
order = exchange.create_order('BTC/USD', 'market', 'buy', 911, None, params)

pprint(order)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/bybit-conditional-orders.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 15
- Comment lines: 2
- Blank lines: 11

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

