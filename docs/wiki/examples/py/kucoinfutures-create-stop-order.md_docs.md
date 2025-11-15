# Documentation: wiki/examples/py/kucoinfutures-create-stop-order.md

## File Metadata

- **Path**: `wiki/examples/py/kucoinfutures-create-stop-order.md`
- **Size**: 1,372 bytes
- **Lines**: 49
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Kucoinfutures Create Stop Order](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint


import ccxt  # noqa: E402
print('CCXT Version:', ccxt.__version__)
exchange = ccxt.kucoinfutures({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_API_SECRET',
    'password': 'YOUR_API_PASSWORD',
    # 'verbose': True,  # for debug output
})

symbol = 'BTC/USDT:USDT'
order_type = 'limit'
side = 'sell'
amount = 1
order_price = 13500  # below the stopLossPrice and above the takeProfitPrice
stop_trigger_params = {
    'triggerPrice': '14000',
    'leverage': 2,  # defaults to 1
}
# stop_loss_params = {
#     'stopLossPrice': '15000',  # the price that triggers the order_price order
#     'leverage': 1,
# }
# take_profit_params = {
#     'takeProfitPrice': '17000',  # the price that triggers the order_price order
#     'leverage': 1,
# }

try:
    stop_trigger_order = exchange.create_order(symbol, order_type, side, amount, order_price, stop_trigger_params)
    # stop_loss_order = exchange.create_order(symbol, order_type, side, amount, order_price, stop_loss_params)
    # take_profit_order = exchange.create_order(symbol, order_type, side, amount, order_price, take_profit_params)
    pprint(stop_trigger_order)
    # pprint(stop_loss_order)
    # pprint(take_profit_order)
except Exception as err:
    print(err)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/kucoinfutures-create-stop-order.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 49
- Code lines: 27
- Comment lines: 14
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

