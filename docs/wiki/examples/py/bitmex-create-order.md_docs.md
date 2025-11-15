# Documentation: wiki/examples/py/bitmex-create-order.md

## File Metadata

- **Path**: `wiki/examples/py/bitmex-create-order.md`
- **Size**: 640 bytes
- **Lines**: 33
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Bitmex Create Order](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


import ccxt  # noqa: E402


exchange = ccxt.bitmex({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})

symbol = 'BTC/USD:BTC-220624'  # bitcoin contract according to https://github.com/ccxt/ccxt/wiki/Manual#symbols-and-market-ids
type = 'StopLimit'  # or 'Market', or 'Stop' or 'StopLimit'
side = 'sell'  # or 'buy'
amount = 1.0
price = 6500.0  # or None

# extra params and overrides
params = {
    'stopPx': 6000.0,  # if needed
}

order = exchange.create_order(symbol, type, side, amount, price, params)
print(order)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/bitmex-create-order.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 33
- Code lines: 20
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

