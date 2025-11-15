# Documentation: wiki/examples/py/huobi-open-close-position-bbo.md

## File Metadata

- **Path**: `wiki/examples/py/huobi-open-close-position-bbo.md`
- **Size**: 1,784 bytes
- **Lines**: 68
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Huobi Open Close Position Bbo](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
from random import randint
import sys
from pprint import pprint


import ccxt.async_support as ccxt  # noqa: E402


print('CCXT Version:', ccxt.__version__)

exchange = ccxt.huobi({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET_KEY',
})

# Example 1 :: Swap : fetch balance, open a position and close it using BBO price
async def example_1():
    markets = await exchange.load_markets(True)

    # fetch swap balance
    balance = await exchange.fetch_balance()
    print(balance)

    # create market order and open position
    symbol = 'ADA/USDT:USDT'
    # type = 'opponent' means it will use BB0 (the best bid or offer on the Exchange) as the price, huobi does not support "market"
    # other types available are: opponent_fok, optimal_5, optimal_10, optimal_20, etc, etc
    # you can check all the types available in the docs: https://huobiapi.github.io/docs/usdt_swap/v1/en/#cross-place-an-order
    type = 'opponent' 
    side = 'buy'
    amount = 1
    price = None
    create_order = await exchange.create_order(symbol, type, side, amount, price)
    print('Create order id:', create_order['id'])

    # check opened position
    symbols = [ symbol ]
    positions = await exchange.fetch_positions(symbols)
    print(positions)

    # Close position by issuing a order in the opposite direction
    side = 'sell'
    params = {
        'reduceOnly': True
    }
    close_position_order = await exchange.createOrder(symbol, type, side, amount, price, params)
    print(close_position_order)
async def main():
    try:
        await example_1()
    except Exception as e:
        print(e)
    await exchange.close()
    

asyncio.run(main())


 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/huobi-open-close-position-bbo.md`.

**Functions defined**: main, example_1

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 68
- Code lines: 41
- Comment lines: 9
- Blank lines: 18

### Main Components

**Functions** (2):
- `example_1()`
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

