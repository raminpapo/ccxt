# Documentation: examples/ccxt.pro/py/okex-create-swap-order.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/okex-create-swap-order.py`
- **Size**: 1,841 bytes
- **Lines**: 51
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

from asyncio import run
import ccxt.pro


print('CCXT Pro Version: ', ccxt.pro.__version__)

exchange = ccxt.pro.okex({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_API_SECRET',
    'password': 'YOUR_API_PASSWORD',
    'options': { 'defaultType': 'swap' },
})


async def main():
    await exchange.load_markets()
    # exchange.verbose = True  # uncomment for debugging

    # https://github.com/ccxt/ccxt/wiki/Manual#overriding-unified-params
    # https://www.okex.com/docs/en/#swap-swap---orders

    symbol = 'BTC/USDT:USDT'
    amount = 1  # how may contracts
    price = None  # or your limit price
    side = 'buy'  # or 'sell'
    future_type = '1'  # 1 open long, 2 open short, 3 close long, 4 close short for futures
    order_type = '4'  # 0 = limit order, 4 = market order

    try:
        # open long market price order
        order = await exchange.create_order(symbol, 'market', side, amount, price, {'type': future_type})
        # --------------------------------------------------------------------
        # open long market price order
        # const order = await exchange.create_order(symbol, type, side, amount, price, {'order_type': order_type})
        # --------------------------------------------------------------------
        # close short market price order
        # const order = await exchange.create_order(symbol, 'market', side, amount, price, {'type': future_type, 'order_type': order_type})
        # --------------------------------------------------------------------
        # close short market price order
        # const order = await exchange.create_order(symbol, '4', side, amount, price, {'order_type': order_type})
        # ...
        print(order)
    except Exception as e:
        print(type(e).__name__, str(e))
    await exchange.close()


run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/okex-create-swap-order.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 51
- Code lines: 24
- Comment lines: 15
- Blank lines: 12

### Main Components

**Functions** (1):
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/ccxt.pro/py/okex-create-swap-order.py
```

