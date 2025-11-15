# Documentation: examples/py/fetch-ticker-many-exchanges-many-symbols.py

## File Metadata

- **Path**: `examples/py/fetch-ticker-many-exchanges-many-symbols.py`
- **Size**: 1,862 bytes
- **Lines**: 63
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys
from asyncio import gather, run

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt.async_support as ccxt  # noqa: E402


print('CCXT Version:', ccxt.__version__)

exchange_ids = ['binance', 'okx', 'gate', 'huobi', 'bitget']
symbols = ['BTC/USDT', 'ETH/USDT', 'LTC/USDT', 'XRP/USDT']
from asyncio import gather, run


async def fetch_price(exchange, symbol):
    try:
        ticker = await exchange.fetch_ticker(symbol)
        return [
            symbol,
            # we use last traded price for this example
            # https://github.com/ccxt/ccxt/wiki/Manual#price-tickers
            # https://github.com/ccxt/ccxt/wiki/Manual#ticker-structure
            ticker['last'],
            'at',
            exchange.id
        ]
    except Exception as e:
        print(type(e).__name__, str(e))
        return [symbol, 'not available at', exchange.id]


async def compare_symbol(exchanges, symbol):
    coroutines = [fetch_price(exchange, symbol) for exchange in exchanges]
    results = await gather(*coroutines)
    print('')  # spacing line
    for result in results:
        print(*result)
    print('')  # spacing line


async def main():
    exchanges = [getattr(ccxt, exchange_id)() for exchange_id in exchange_ids]
    # https://github.com/ccxt/ccxt/wiki/Manual#loading-markets
    load_markets = [exchange.load_markets() for exchange in exchanges]
    print('Loading markets...')
    await gather(*load_markets)
    print('Done loading markets.')
    print('Loading tickers...')
    coroutines = [compare_symbol(exchanges, symbol) for symbol in symbols]
    await gather(*coroutines)
    close_all = [exchange.close() for exchange in exchanges]
    await gather(*close_all)



if __name__ == '__main__':
    run(main())

```

## High-Level Overview

This is a Python file located at `examples/py/fetch-ticker-many-exchanges-many-symbols.py`.

**Functions defined**: compare_symbol, fetch_price, main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 63
- Code lines: 42
- Comment lines: 5
- Blank lines: 16

### Main Components

**Functions** (3):
- `compare_symbol()`
- `fetch_price()`
- `main()`



## Usage Examples

### Main execution block:

```python
run(main())
```



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/fetch-ticker-many-exchanges-many-symbols.py
```

