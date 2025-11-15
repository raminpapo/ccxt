# Documentation: examples/py/async-binance-futures-vs-spot.py

## File Metadata

- **Path**: `examples/py/async-binance-futures-vs-spot.py`
- **Size**: 1,386 bytes
- **Lines**: 48
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import asyncio
import os
import sys
from pprint import pprint

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt.async_support as ccxt  # noqa: E402


async def load(exchange, symbol, type='spot'):
    exchange.options['defaultType'] = type
    await exchange.load_markets(True)
    try:
        return {
            'balance': await exchange.fetch_balance(),
            # you actually want pagination here
            # https://github.com/ccxt/ccxt/wiki/Manual#pagination
            # but this will do as an example, tweak it for your needs
            'orders': await exchange.fetch_orders(symbol),
            'open orders': await exchange.fetch_open_orders(symbol),
            'closed orders': await exchange.fetch_closed_orders(symbol),
            'my trades': await exchange.fetch_my_trades(symbol),
        }
    except Exception as e:
        print('\n\nError in load() with type =', type, '-', e)
        raise e


async def run():
    exchange = ccxt.binance({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
    })
    symbol = 'BTC/USDT'
    everything = {
        'spot': await load(exchange, symbol, 'spot'),
        'future': await load(exchange, symbol, 'future'),
    }
    await exchange.close()
    return everything


asyncio.run(run())

```

## High-Level Overview

This is a Python file located at `examples/py/async-binance-futures-vs-spot.py`.

**Functions defined**: run, load

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 48
- Code lines: 34
- Comment lines: 4
- Blank lines: 10

### Main Components

**Functions** (2):
- `load()`
- `run()`



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
python examples/py/async-binance-futures-vs-spot.py
```

