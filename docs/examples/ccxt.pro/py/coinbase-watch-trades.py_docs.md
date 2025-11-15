# Documentation: examples/ccxt.pro/py/coinbase-watch-trades.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/coinbase-watch-trades.py`
- **Size**: 871 bytes
- **Lines**: 28
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import ccxt.pro
from asyncio import run

async def main():
    exchange = ccxt.pro.coinbase()
    method = 'watchTrades'
    print('CCXT Pro version', ccxt.pro.__version__)
    if exchange.has[method]:
        while True:
            try:
                trades = await exchange.watch_trades('BTC/USD')
                num_trades = len(trades)
                trade = trades[-1]
                print(exchange.iso8601(exchange.milliseconds()), trade['symbol'], trade['datetime'], trade['price'], trade['amount'], 'stored', num_trades, 'trades in cache')
            except Exception as e:
                # stop
                await exchange.close()
                raise e
                # or retry
                # pass
    else:
        raise Exception(exchange.id + ' ' + method + ' is not supported or not implemented yet')


run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/coinbase-watch-trades.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 19
- Comment lines: 4
- Blank lines: 5

### Main Components

**Functions** (1):
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations
- ✓ Implements caching mechanisms



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/ccxt.pro/py/coinbase-watch-trades.py
```

