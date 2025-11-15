# Documentation: examples/ccxt.pro/py/watch-ticker-to-csv.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/watch-ticker-to-csv.py`
- **Size**: 1,536 bytes
- **Lines**: 46
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

from asyncio import gather, run
import ccxt.pro
from pprint import pprint


async def watch_ticker_continuously(exchange, symbol):
    filename = exchange.id + '-' + symbol.replace('/', '-') + '.csv'
    print('Watching', exchange.id, symbol, filename)
    keys = ['index', 'exchange', 'symbol', 'timestamp', 'open', 'high', 'low', 'close', 'baseVolume']
    with open(filename, 'w') as file:
        file.write(','.join(keys) + "\n")
    index = 0
    while True:
        try:
            ticker = await exchange.watch_ticker(symbol)
            values = [str(index), exchange.id] + [str(ticker[key]) for key in keys[2:]]
            print(*values)
            with open(filename, 'a') as file:
                file.write(','.join(values) + "\n")
            index += 1
        except Exception as e:
            print(e)


async def watch_tickers_continuously(exchange_id, overrides, symbols):
    exchange_class = getattr(ccxt.pro, exchange_id)
    exchange = exchange_class(overrides)
    coroutines = [watch_ticker_continuously(exchange, symbol) for symbol in symbols]
    await gather(*coroutines)
    await exchange.close()


async def main():
    exchanges = {
        'binance': {'options': {'defaultType': 'future'}},
        'huobipro': {}
    }
    symbols = ['BTC/USDT', 'ETH/USDT', 'LTC/USDT', 'XRP/USDT', 'BCH/USDT']
    coroutines = [watch_tickers_continuously(exchange_id, exchanges[exchange_id], symbols) for exchange_id in exchanges.keys()]
    return await gather(*coroutines)


run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/watch-ticker-to-csv.py`.

**Functions defined**: watch_ticker_continuously, watch_tickers_continuously, main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 46
- Code lines: 35
- Comment lines: 1
- Blank lines: 10

### Main Components

**Functions** (3):
- `main()`
- `watch_ticker_continuously()`
- `watch_tickers_continuously()`



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
python examples/ccxt.pro/py/watch-ticker-to-csv.py
```

