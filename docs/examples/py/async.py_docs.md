# Documentation: examples/py/async.py

## File Metadata

- **Path**: `examples/py/async.py`
- **Size**: 897 bytes
- **Lines**: 35
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import asyncio
import functools
import os
import sys

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt.async_support as ccxt  # noqa: E402


async def print_ticker(symbol, id):
    # verbose mode will show the order of execution to verify concurrency
    exchange = getattr(ccxt, id)({'verbose': True})
    print(await exchange.fetch_ticker(symbol))
    await exchange.close()


if __name__ == '__main__':

    symbol = 'ETH/BTC'
    print_ethbtc_ticker = functools.partial(print_ticker, symbol)
    [asyncio.ensure_future(print_ethbtc_ticker(id)) for id in [
        'bitfinex',
        'poloniex',
        'kraken',
        'bittrex',
        'hitbtc',
    ]]
    loop = asyncio.get_event_loop()
    pending = asyncio.all_tasks(loop)
    loop.run_until_complete(asyncio.gather(*pending))

```

## High-Level Overview

This is a Python file located at `examples/py/async.py`.

**Functions defined**: print_ticker

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 24
- Comment lines: 2
- Blank lines: 9

### Main Components

**Functions** (1):
- `print_ticker()`



## Usage Examples

### Main execution block:

```python
symbol = 'ETH/BTC'
    print_ethbtc_ticker = functools.partial(print_ticker, symbol)
    [asyncio.ensure_future(print_ethbtc_ticker(id)) for id in [
        'bitfinex',
        'poloniex',
        'kraken',
        'bittrex',
        'hitbtc',
    ]]
    loop = asyncio.get_event_loop()
    pending = asyncio.all_tasks(loop)
    loop.run_until_complete(asyncio.gather(*pending))
```



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/async.py
```

