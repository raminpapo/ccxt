# Documentation: wiki/examples/py/coinex-futures.md

## File Metadata

- **Path**: `wiki/examples/py/coinex-futures.md`
- **Size**: 2,397 bytes
- **Lines**: 87
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Coinex Futures](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
from random import randint
import sys
from pprint import pprint


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
async def main():
    await example_1()
    await example_2()

asyncio.run(main())


 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/coinex-futures.md`.

**Functions defined**: main, example_1, example_2

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 87
- Code lines: 56
- Comment lines: 10
- Blank lines: 21

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

**To execute this Markdown file:**

