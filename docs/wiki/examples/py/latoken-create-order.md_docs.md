# Documentation: wiki/examples/py/latoken-create-order.md

## File Metadata

- **Path**: `wiki/examples/py/latoken-create-order.md`
- **Size**: 429 bytes
- **Lines**: 29
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Latoken Create Order](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


import ccxt  # noqa: E402


exchange = ccxt.latoken({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})

symbol = 'ETH/BTC'
type = 'limit'  # only support limit
side = 'buy'  # or 'sell'
amount = 0.01
price = 0.015881  # or None

order = exchange.create_order(symbol, type, side, amount, price)

print(order)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/latoken-create-order.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 17
- Comment lines: 1
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

