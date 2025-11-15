# Documentation: wiki/examples/py/bybit-USDC-create-option-order.md

## File Metadata

- **Path**: `wiki/examples/py/bybit-USDC-create-option-order.md`
- **Size**: 657 bytes
- **Lines**: 32
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Bybit Usdc Create Option Order](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint


import ccxt  # noqa: E402
print('CCXT Version:', ccxt.__version__)
exchange = ccxt.bybit ({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_API_SECRET',
    'defaultType': 'option',
    # 'verbose': True,  # for debug output
})

# BASE/QUOTE:SETTLE-YYMMDD-STRIKE-C (end with C for call, end with P for put)
symbol = 'BTC/USD:USDC-221209-18000-C'
amount = 0.01
price = 280.0

try:
    order = exchange.create_order(symbol, 'limit', 'buy', amount, price)
    pprint(order)
except Exception as err:
    print(err)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/bybit-USDC-create-option-order.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 21
- Comment lines: 3
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

