# Documentation: wiki/examples/py/async-fetch-many-orderbooks-continuously.md

## File Metadata

- **Path**: `wiki/examples/py/async-fetch-many-orderbooks-continuously.md`
- **Size**: 1,443 bytes
- **Lines**: 51
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Fetch Many Orderbooks Continuously](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from asyncio import gather, run


import ccxt.async_support as ccxt  # noqa: E402


async def symbol_loop(exchange, symbol):
    print('Starting the', exchange.id, 'symbol loop with', symbol)
    while True:
        try:
            orderbook = await exchange.fetch_order_book(symbol)
            now = exchange.milliseconds()
            print(exchange.iso8601(now), exchange.id, symbol, orderbook['asks'][0], orderbook['bids'][0])

            # --------------------> DO YOUR LOGIC HERE <------------------

        except Exception as e:
            print(str(e))
            # raise e  # uncomment to break all loops in case of an error in any one of them
            break  # you can break just this one loop if it fails


async def exchange_loop(exchange_id, symbols):
    print('Starting the', exchange_id, 'exchange loop with', symbols)
    exchange = getattr(ccxt, exchange_id)()
    loops = [symbol_loop(exchange, symbol) for symbol in symbols]
    await gather(*loops)
    await exchange.close()


async def main():
    exchanges = {
        'okex': ['BTC/USDT', 'ETH/BTC', 'ETH/USDT'],
        'binance': ['BTC/USDT', 'ETH/BTC'],
        'bitfinex': ['BTC/USDT'],
    }
    loops = [exchange_loop(exchange_id, symbols) for exchange_id, symbols in exchanges.items()]
    await gather(*loops)


run(main())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-fetch-many-orderbooks-continuously.md`.

**Functions defined**: exchange_loop, main, symbol_loop

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 51
- Code lines: 32
- Comment lines: 3
- Blank lines: 16

### Main Components

**Functions** (3):
- `exchange_loop()`
- `main()`
- `symbol_loop()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

