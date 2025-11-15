# Documentation: examples/py/async-orderbooks.py

## File Metadata

- **Path**: `examples/py/async-orderbooks.py`
- **Size**: 1,485 bytes
- **Lines**: 44
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


async def async_client(exchange, symbol):
    client = getattr(ccxta, exchange)()
    await client.load_markets()
    if symbol not in client.symbols:
        raise Exception(exchange + ' does not support symbol ' + symbol)
    while True:
        try:
            orderbook = await client.fetch_order_book(symbol)
            datetime = client.iso8601(client.milliseconds())
            print(datetime, client.id, symbol, orderbook['bids'][0], orderbook['asks'][0])
        except Exception as e:
            print(type(e).__name__, e.args, str(e))  # comment if not needed
            # break  # uncomment to break it
            # pass   # uncomment to do nothing and just retry again on next iteration
            # or add your own reaction according to the purpose of your app
    await client.close()


async def multi_orderbooks(exchanges, symbol):
    input_coroutines = [async_client(exchange, symbol) for exchange in exchanges]
    await asyncio.gather(*input_coroutines, return_exceptions=True)


if __name__ == '__main__':

    # Consider review request rate limit in the methods you call
    exchanges = ["bittrex", "bitfinex", "poloniex"]
    symbol = 'ETH/BTC'

    asyncio.run(multi_orderbooks(exchanges, symbol))

```

## High-Level Overview

This is a Python file located at `examples/py/async-orderbooks.py`.

**Functions defined**: async_client, multi_orderbooks

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 28
- Comment lines: 5
- Blank lines: 11

### Main Components

**Functions** (2):
- `async_client()`
- `multi_orderbooks()`



## Usage Examples

### Main execution block:

```python
# Consider review request rate limit in the methods you call
    exchanges = ["bittrex", "bitfinex", "poloniex"]
    symbol = 'ETH/BTC'

    asyncio.run(multi_orderbooks(exchanges, symbol))
```



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/async-orderbooks.py
```

