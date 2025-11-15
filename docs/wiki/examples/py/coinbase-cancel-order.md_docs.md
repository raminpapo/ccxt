# Documentation: wiki/examples/py/coinbase-cancel-order.md

## File Metadata

- **Path**: `wiki/examples/py/coinbase-cancel-order.md`
- **Size**: 690 bytes
- **Lines**: 31
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Coinbase Cancel Order](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint


import ccxt  # noqa: E402
print('CCXT Version:', ccxt.__version__)
exchange = ccxt.coinbase({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_API_SECRET',
    # 'verbose': True,  # for debug output
})

order_id = '04204eaf-94d6-444a-b9b7-2f8a485311f6'
# order_ids = ['04204eaf-94d6-444a-b9b7-2f8a485311f6', '7c13a059-d235-46e1-ab43-6794a5836db9']

try:
    cancel_order = exchange.cancel_order(order_id)
    # cancel_orders = exchange.cancel_orders(order_ids)
    pprint(cancel_order)
    # pprint(cancel_orders)
except Exception as err:
    print(err)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/coinbase-cancel-order.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 18
- Comment lines: 5
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

