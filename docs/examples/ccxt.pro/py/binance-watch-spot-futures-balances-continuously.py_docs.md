# Documentation: examples/ccxt.pro/py/binance-watch-spot-futures-balances-continuously.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/binance-watch-spot-futures-balances-continuously.py`
- **Size**: 1,490 bytes
- **Lines**: 49
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

from asyncio import run, gather
import os
import sys

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt.pro  # noqa: E402


print('CCXT Version:', ccxt.__version__)


async def print_balance_continuously(exchange):
    while True:
        try:
            print('-----------------------------------------------------------')
            await exchange.load_markets()
            balance = await exchange.watch_balance()
            print(exchange.iso8601(exchange.milliseconds()), exchange.id)
            for currency, value in balance['total'].items():
                print(value, currency)
        except Exception as e:
            print('-----------------------------------------------------------')
            print(exchange.iso8601(exchange.milliseconds()), exchange.id, type(e), e)
            await exchange.sleep(300000)  # sleep 5 minutes and retry


async def main():
    config = {
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
    }
    exchange_ids = [
        'binance',
        'binanceusdm',
        'binancecoinm',
    ]
    exchanges = [getattr(ccxt.pro, exchange_id)(config) for exchange_id in exchange_ids]
    printing_loops = [print_balance_continuously(exchange) for exchange in exchanges]
    await gather(*printing_loops)
    closing_tasks = [exchange.close() for exchange in exchanges]
    await gather(*closing_tasks)


run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/binance-watch-spot-futures-balances-continuously.py`.

**Functions defined**: print_balance_continuously, main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 49
- Code lines: 36
- Comment lines: 1
- Blank lines: 12

### Main Components

**Functions** (2):
- `main()`
- `print_balance_continuously()`



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
python examples/ccxt.pro/py/binance-watch-spot-futures-balances-continuously.py
```

