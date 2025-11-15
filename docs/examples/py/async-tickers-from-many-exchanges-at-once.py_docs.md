# Documentation: examples/py/async-tickers-from-many-exchanges-at-once.py

## File Metadata

- **Path**: `examples/py/async-tickers-from-many-exchanges-at-once.py`
- **Size**: 1,184 bytes
- **Lines**: 47
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


def sync_client(exchange):
    client = getattr(ccxt, exchange)()
    tickers = client.fetch_tickers()
    return tickers


async def async_client(exchange):
    client = getattr(ccxta, exchange)()
    tickers = await client.fetch_tickers()
    await client.close()
    return tickers


async def multi_tickers(exchanges):
    input_coroutines = [async_client(exchange) for exchange in exchanges]
    tickers = await asyncio.gather(*input_coroutines, return_exceptions=True)
    return tickers


if __name__ == '__main__':

    # Consider review request rate limit in the methods you call
    exchanges = ["coinex", "bittrex", "bitfinex", "poloniex", "hitbtc"]

    tic = time.time()
    a = asyncio.run(multi_tickers(exchanges))
    print("async call spend:", time.time() - tic)

    time.sleep(1)

    tic = time.time()
    a = [sync_client(exchange) for exchange in exchanges]
    print("sync call spend:", time.time() - tic)

```

## High-Level Overview

This is a Python file located at `examples/py/async-tickers-from-many-exchanges-at-once.py`.

**Functions defined**: multi_tickers, async_client, sync_client

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 30
- Comment lines: 2
- Blank lines: 15

### Main Components

**Functions** (3):
- `async_client()`
- `multi_tickers()`
- `sync_client()`



## Usage Examples

### Main execution block:

```python
# Consider review request rate limit in the methods you call
    exchanges = ["coinex", "bittrex", "bitfinex", "poloniex", "hitbtc"]

    tic = time.time()
    a = asyncio.run(multi_tickers(exchanges))
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
python examples/py/async-tickers-from-many-exchanges-at-once.py
```

