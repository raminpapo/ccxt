# Documentation: examples/py/coinex-futures.py

## File Metadata

- **Path**: `examples/py/coinex-futures.py`
- **Size**: 2,651 bytes
- **Lines**: 90
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import asyncio
import os
from random import randint
import sys
from pprint import pprint

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt.async_support as ccxt  # noqa: E402


print('CCXT Version:', ccxt.__version__)

exchange = ccxt.coinex({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET_KEY',
})

# Example 1 :: Swap : fetch balance, create a limit swap order with leverage
async def example_1():
    exchange.options['defaultType'] = 'swap'
    exchange.options['defaultMarginMode'] = 'cross' # or isolated
    markets = await exchange.load_markets()

    # fetch swap balance
    balance = await exchange.fetch_balance()
    print(balance)
    
    # set the desired leverage (has to be made before placing the order and for a specific symbol)
    leverage = 8
    symbol = 'ADA/USDT:USDT'
    leverage_response = await exchange.set_leverage(leverage, symbol)

    # create limit order
    symbol = 'ADA/USDT:USDT'
    type = 'limit'
    side = 'buy'
    amount = 50
    price = 0.3
    create_order = await exchange.create_order(symbol, type, side, amount, price)
    print('Create order id:', create_order['id'])

# ------------------------------------------------------------------------------------------

# Example 2 :: Swap :: open a position and close it
async def example_2():
    exchange.options['defaultType'] = 'swap'; # very important set swap as default type
    exchange.options['defaultMarginMode'] = 'cross' # or isolated
    markets = await exchange.load_markets()


    # set the desired leverage (has to be made before placing the order and for a specific symbol)
    leverage = 3
    symbol = 'ADA/USDT:USDT'
    leverage_response = await exchange.set_leverage(leverage, symbol)

    # create market order and open position
    symbol = 'ADA/USDT:USDT'
    type = 'market'
    side = 'buy'
    amount = 55
    price = None
    create_order = await exchange.create_order(symbol, type, side, amount, price)
    print('Create order id:', create_order['id'])

    # check opened position
    position = await exchange.fetch_position(symbol)
    print(position)

    # Close position by issuing a market order in the opposite direction
    side = 'sell'
    params = {
        'reduce_only': True
    }
    close_position_order = await exchange.createOrder(symbol, type, side, amount, price, params)
    print(close_position_order)

# ------------------------------------------------------------------------------------------

async def main():
    await example_1()
    await example_2()

asyncio.run(main())



```

## High-Level Overview

This is a Python file located at `examples/py/coinex-futures.py`.

**Functions defined**: main, example_1, example_2

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 90
- Code lines: 55
- Comment lines: 12
- Blank lines: 23

### Main Components

**Functions** (3):
- `example_1()`
- `example_2()`
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
python examples/py/coinex-futures.py
```

