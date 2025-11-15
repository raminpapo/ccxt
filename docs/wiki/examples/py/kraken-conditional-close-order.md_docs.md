# Documentation: wiki/examples/py/kraken-conditional-close-order.md

## File Metadata

- **Path**: `wiki/examples/py/kraken-conditional-close-order.md`
- **Size**: 890 bytes
- **Lines**: 48
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Kraken Conditional Close Order](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


import ccxt  # noqa: E402
from pprint import pprint


exchange = ccxt.kraken({
    # 'apiKey': 'YOUR_API_KEY',
    # 'secret': 'YOUR_SECRET',
})

markets = exchange.load_markets()

exchange.verbose = True

symbol = 'XMR/USD'
ticker = exchange.fetch_ticker(symbol)
last_price = ticker['last']

# extra params and overrides
params = {
    'close': {
        'ordertype': 'limit',
        'price': last_price * 1.3,
    }
}
amount = 0.05
price = last_price * 0.7
order = exchange.create_order(symbol, 'limit', 'buy', amount, price, params)
print('Created order:')
pprint(order)

fetched_order = exchange.fetch_order(order['id'])
print('Fetched order:')
pprint(fetched_order)

canceled_order = exchange.cancel_order(order['id'])
print('Canceled order:')
pprint(canceled_order) 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/kraken-conditional-close-order.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 48
- Code lines: 31
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

