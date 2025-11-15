# Documentation: wiki/examples/py/async-fetch-order-book-from-many-exchanges.md

## File Metadata

- **Path**: `wiki/examples/py/async-fetch-order-book-from-many-exchanges.md`
- **Size**: 1,289 bytes
- **Lines**: 54
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Fetch Order Book From Many Exchanges](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys
from pprint import pprint


import ccxt.async_support as ccxt  # noqa: E402


exchange_ids = [ 'binance', 'kucoin', 'huobipro' ]
symbol = 'ETH/BTC'

async def loop(exchange_id, symbol):

    exchange_class = getattr(ccxt, exchange_id)
    exchange = exchange_class()
    orderbook = {}
    try:
        await exchange.load_markets()
        # exchange.verbose = True  # uncomment for debugging purposes
        orderbook = await exchange.fetch_order_book(symbol)
    except Exception as e:
        print(type(e).__name__, str(e))
    await exchange.close()
    return exchange.extend (orderbook, {
        'exchange_id': exchange_id,
        'symbol': symbol,
    })


async def run(exchange_ids, symbol):
    coroutines = [loop(exchange_id, symbol) for exchange_id in exchange_ids]
    return await asyncio.gather(*coroutines)


main = run(exchange_ids, symbol)
results = asyncio.run(main)
for result in results:
    bids = result['bids']
    asks = result['asks']
    print(
        result['exchange_id'],
        result['symbol'],
        'top bid', bids[0], 'of', len(bids), 'bids,',
        'top ask', asks[0], 'of', len(asks), 'asks'
    )
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-fetch-order-book-from-many-exchanges.md`.

**Functions defined**: loop, run

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 54
- Code lines: 38
- Comment lines: 2
- Blank lines: 14

### Main Components

**Functions** (2):
- `loop()`
- `run()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

