# Documentation: examples/py/async-tickers.py

## File Metadata

- **Path**: `examples/py/async-tickers.py`
- **Size**: 1,359 bytes
- **Lines**: 42
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import asyncio
import os
import sys

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt.async_support as ccxt  # noqa: E402


def get_active_symbols(exchange):
    return [symbol for symbol in exchange.symbols if is_active_symbol(exchange, symbol)]


def is_active_symbol(exchange, symbol):
    return ('.' not in symbol) and (('active' not in exchange.markets[symbol]) or (exchange.markets[symbol]['active']))


async def fetch_ticker(exchange, symbol):
    ticker = await exchange.fetchTicker(symbol)
    print(exchange.id, symbol, ticker)
    return ticker


async def fetch_tickers(exchange):
    await exchange.load_markets()
    print(exchange.id, 'fetching all tickers by simultaneous multiple concurrent requests')
    symbols_to_load = get_active_symbols(exchange)
    input_coroutines = [fetch_ticker(exchange, symbol) for symbol in symbols_to_load]
    tickers = await asyncio.gather(*input_coroutines, return_exceptions=True)
    for ticker, symbol in zip(tickers, symbols_to_load):
        if not isinstance(ticker, dict):
            print(exchange.id, symbol, 'error')
        else:
            print(exchange.id, symbol, 'ok')
    print(exchange.id, 'fetched', len(list(tickers)), 'tickers')


asyncio.run(fetch_tickers(ccxt.bitfinex()))

```

## High-Level Overview

This is a Python file located at `examples/py/async-tickers.py`.

**Functions defined**: fetch_tickers, is_active_symbol, fetch_ticker, get_active_symbols

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 42
- Code lines: 27
- Comment lines: 1
- Blank lines: 14

### Main Components

**Functions** (4):
- `fetch_ticker()`
- `fetch_tickers()`
- `get_active_symbols()`
- `is_active_symbol()`



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
python examples/py/async-tickers.py
```

