# Documentation: wiki/examples/py/async-tickers-from-many-exchanges-at-once.md

## File Metadata

- **Path**: `wiki/examples/py/async-tickers-from-many-exchanges-at-once.md`
- **Size**: 1,147 bytes
- **Lines**: 50
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Tickers From Many Exchanges At Once](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import ccxt
import ccxt.async_support as ccxta  # noqa: E402
import time
import os
import sys



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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-tickers-from-many-exchanges-at-once.md`.

**Functions defined**: multi_tickers, async_client, sync_client

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 50
- Code lines: 31
- Comment lines: 2
- Blank lines: 17

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

**To execute this Markdown file:**

