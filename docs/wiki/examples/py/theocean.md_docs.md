# Documentation: wiki/examples/py/theocean.md

## File Metadata

- **Path**: `wiki/examples/py/theocean.md`
- **Size**: 1,050 bytes
- **Lines**: 46
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Theocean](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


import ccxt  # noqa: E402

walletAddress = os.environ['WALLET_ADDRESS']
privateKey = os.environ['PRIVATE_KEY']
apiKey = os.environ['API_KEY']
secret = os.environ['SECRET']
ocean = ccxt.theocean({
    'walletAddress': walletAddress,
    'privateKey': privateKey,
    'apiKey': apiKey,
    'secret': secret
})

# get balance
balance = ocean.fetch_balance_by_code('REP')
print('REP balance: ', balance)

# get order book
order_book = ocean.fetch_order_book('REP/ZRX')
print('REP/ZRX orderbook: ', order_book)

# placing order
place_result = ocean.create_order('REP/ZRX', 'limit', 'sell', '0.5', '30')
id = place_result['id']
print('result of placing order: ', place_result)

# cancel order
if place_result['remaining'] > 0:
    cancel_result = ocean.cancel_order(id)
    print('cancel result: ', cancel_result)

# cancel all open user orders
cancel_all_orders_result = ocean.cancel_all_orders()
print('cancel all orders result: ', cancel_all_orders_result)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/theocean.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 46
- Code lines: 28
- Comment lines: 6
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

