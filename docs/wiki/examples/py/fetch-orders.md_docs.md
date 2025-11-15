# Documentation: wiki/examples/py/fetch-orders.md

## File Metadata

- **Path**: `wiki/examples/py/fetch-orders.md`
- **Size**: 356 bytes
- **Lines**: 25
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Fetch Orders](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


import ccxt  # noqa: E402

exchange = ccxt.bittrex({
    "apiKey": "YOUR_API_KEY",
    "secret": "YOUR_API_SECRET",
    "enableRateLimit": True,
})

orders = exchange.fetch_orders()
print(orders)

order = exchange.fetch_order(orders[0]['id'])
print(order)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/fetch-orders.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 15
- Comment lines: 1
- Blank lines: 9

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

