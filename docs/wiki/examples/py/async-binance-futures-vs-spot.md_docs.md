# Documentation: wiki/examples/py/async-binance-futures-vs-spot.md

## File Metadata

- **Path**: `wiki/examples/py/async-binance-futures-vs-spot.md`
- **Size**: 1,337 bytes
- **Lines**: 51
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Binance Futures Vs Spot](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys
from pprint import pprint


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-binance-futures-vs-spot.md`.

**Functions defined**: run, load

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 51
- Code lines: 35
- Comment lines: 4
- Blank lines: 12

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

**To execute this Markdown file:**

