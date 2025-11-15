# Documentation: wiki/examples/py/phemex-create-stop-order.md

## File Metadata

- **Path**: `wiki/examples/py/phemex-create-stop-order.md`
- **Size**: 738 bytes
- **Lines**: 46
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Phemex Create Stop Order](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


import ccxt  # noqa: E402

exchange = ccxt.phemex({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})

# exchange.set_sandbox_mode(True)

# Example 1: Creating stop-market order
symbol = 'LTC/USDT'
type = 'market'
side = 'buy'
amount = 0.5

params = {
    'stopPrice': 50,
}

stop_market = exchange.create_order(symbol, type, side, amount, None, params)
print(stop_market)

# Example 2: Create stop-limit order
symbol = 'LTC/USDT'
type = 'limit'
side = 'buy'
amount = 0.5
price = 70

params = {
    'stopPrice': 50,
}

stop_limit = exchange.create_order(symbol, type, side, amount, price, params)
print(stop_limit) 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/phemex-create-stop-order.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 46
- Code lines: 29
- Comment lines: 4
- Blank lines: 13

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

