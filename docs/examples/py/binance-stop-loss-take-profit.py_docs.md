# Documentation: examples/py/binance-stop-loss-take-profit.py

## File Metadata

- **Path**: `examples/py/binance-stop-loss-take-profit.py`
- **Size**: 1,086 bytes
- **Lines**: 43
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt  # noqa: E402

exchange = ccxt.binanceusdm({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})

markets = exchange.load_markets()
# exchange.verbose = True  # uncomment for debugging purposes

symbol = 'BTC/USDT'
side = 'buy'
amount = 0.01
price = None
stopLossPrice = 25000
takeProfitPrice = 35000

try:

    order = exchange.create_order(symbol, 'MARKET', side, amount)
    print(order)

    inverted_side = 'sell' if side == 'buy' else 'buy'

    stopLossParams = {'stopPrice': stopLossPrice}
    stopLossOrder = exchange.create_order(symbol, 'STOP_MARKET', inverted_side, amount, price, stopLossParams)
    print(stopLossOrder)

    takeProfitParams = {'stopPrice': takeProfitPrice}
    takeProfitOrder = exchange.create_order(symbol, 'TAKE_PROFIT_MARKET', inverted_side, amount, price, takeProfitParams)
    print(takeProfitOrder)

except Exception as e:
    print(type(e).__name__, str(e))

```

## High-Level Overview

This is a Python file located at `examples/py/binance-stop-loss-take-profit.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 43
- Code lines: 28
- Comment lines: 2
- Blank lines: 13

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/binance-stop-loss-take-profit.py
```

