# Documentation: examples/py/async-orderbooks-from-multiple-exchanges-at-once.py

## File Metadata

- **Path**: `examples/py/async-orderbooks-from-multiple-exchanges-at-once.py`
- **Size**: 1,724 bytes
- **Lines**: 61
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import asyncio
import ccxt
import ccxt.async_support as ccxta  # noqa: E402
import time
import os
import sys

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

symbol = 'ETH/BTC'


def sync_client(exchange_id):
    orderbook = None
    exchange = getattr(ccxt, exchange_id)()
    try:
        exchange.load_markets()
        market = exchange.market(symbol)
        orderbook = exchange.fetch_order_book(market['symbol'])
    except Exception as e:
        print(type(e).__name__, str(e))
    return { 'exchange': exchange.id, 'orderbook': orderbook }


async def async_client(exchange_id):
    orderbook = None
    exchange = getattr(ccxta, exchange_id)()
    try:
        await exchange.load_markets()
        market = exchange.market(symbol)
        orderbook = await exchange.fetch_order_book(market['symbol'])
    except Exception as e:
        print(type(e).__name__, str(e))
    await exchange.close()
    return { 'exchange': exchange.id, 'orderbook': orderbook }


async def multi_orderbooks(exchanges):
    input_coroutines = [async_client(exchange) for exchange in exchanges]
    orderbooks = await asyncio.gather(*input_coroutines, return_exceptions=True)
    return orderbooks


if __name__ == '__main__':

    # Consider review request rate limit in the methods you call
    exchanges = ["kucoin", "bittrex", "bitfinex", "poloniex", "huobipro"]

    tic = time.time()
    a = asyncio.run(multi_orderbooks(exchanges))
    print("async call spend:", time.time() - tic)

    time.sleep(1)

    tic = time.time()
    a = [sync_client(exchange) for exchange in exchanges]
    print("sync call spend:", time.time() - tic)

```

## High-Level Overview

This is a Python file located at `examples/py/async-orderbooks-from-multiple-exchanges-at-once.py`.

**Functions defined**: async_client, multi_orderbooks, sync_client

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 61
- Code lines: 43
- Comment lines: 2
- Blank lines: 16

### Main Components

**Functions** (3):
- `async_client()`
- `multi_orderbooks()`
- `sync_client()`



## Usage Examples

### Main execution block:

```python
# Consider review request rate limit in the methods you call
    exchanges = ["kucoin", "bittrex", "bitfinex", "poloniex", "huobipro"]

    tic = time.time()
    a = asyncio.run(multi_orderbooks(exchanges))
    print("async call spend:", time.time() - tic)

    time.sleep(1)

    tic = time.time()
    a = [sync_client(exchange) for exchange in exchanges]
    print("sync call spend:", time.time() - tic)
```



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/async-orderbooks-from-multiple-exchanges-at-once.py
```

