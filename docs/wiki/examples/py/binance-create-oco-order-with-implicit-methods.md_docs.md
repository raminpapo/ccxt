# Documentation: wiki/examples/py/binance-create-oco-order-with-implicit-methods.md

## File Metadata

- **Path**: `wiki/examples/py/binance-create-oco-order-with-implicit-methods.md`
- **Size**: 1,408 bytes
- **Lines**: 43
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Binance Create Oco Order With Implicit Methods](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


import ccxt  # noqa: E402


exchange = ccxt.binance({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
    # 'options': {'adjustForTimeDifference': True}
})

symbol = 'SCRT/BTC'
market = exchange.market(symbol)
amount = 26
price = 0.00002
stop_price = 0.000016
stop_limit_price = 0.000015

response = exchange.private_post_order_oco({
    'symbol': market['id'],
    'side': 'SELL',  # SELL, BUY
    'quantity': exchange.amount_to_precision(symbol, amount),
    'price': exchange.price_to_precision(symbol, price),
    'stopPrice': exchange.price_to_precision(symbol, stop_price),
    'stopLimitPrice': exchange.price_to_precision(symbol, stop_limit_price),  # If provided, stopLimitTimeInForce is required
    'stopLimitTimeInForce': 'GTC',  # GTC, FOK, IOC
    # 'listClientOrderId': exchange.uuid(),  # A unique Id for the entire orderList
    # 'limitClientOrderId': exchange.uuid(),  # A unique Id for the limit order
    # 'limitIcebergQty': exchangea.amount_to_precision(symbol, limit_iceberg_quantity),
    # 'stopClientOrderId': exchange.uuid()  # A unique Id for the stop loss/stop loss limit leg
    # 'stopIcebergQty': exchange.amount_to_precision(symbol, stop_iceberg_quantity),
    # 'newOrderRespType': 'ACK',  # ACK, RESULT, FULL
})
print(response) 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/binance-create-oco-order-with-implicit-methods.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 43
- Code lines: 26
- Comment lines: 8
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

