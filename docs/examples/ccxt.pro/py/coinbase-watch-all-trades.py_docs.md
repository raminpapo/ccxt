# Documentation: examples/ccxt.pro/py/coinbase-watch-all-trades.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/coinbase-watch-all-trades.py`
- **Size**: 913 bytes
- **Lines**: 31
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
        last_id = ''
        while True:
            try:
                trades = await exchange.watch_trades('BTC/USD')
                for trade in trades:
                    if trade['id'] > last_id:
                        print(exchange.iso8601(exchange.milliseconds()), trade['symbol'], trade['datetime'], trade['price'], trade['amount'])
                        last_id = trade['id']

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

This is a Python file located at `examples/ccxt.pro/py/coinbase-watch-all-trades.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 21
- Comment lines: 4
- Blank lines: 6

### Main Components

**Functions** (1):
- `main()`



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
python examples/ccxt.pro/py/coinbase-watch-all-trades.py
```

