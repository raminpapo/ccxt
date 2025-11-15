# Documentation: wiki/examples/py/async-theocean-tickers.md

## File Metadata

- **Path**: `wiki/examples/py/async-theocean-tickers.md`
- **Size**: 1,354 bytes
- **Lines**: 47
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Theocean Tickers](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys


import ccxt.async_support as ccxt  # noqa: E402


def get_active_symbols(exchange):
    return [symbol for symbol in exchange.symbols if is_active_symbol(exchange, symbol)]


def is_active_symbol(exchange, symbol):
    return ('.' not in symbol) and (('active' not in exchange.markets[symbol]) or (exchange.markets[symbol]['active']))


async def fetch_ticker(exchange, symbol):
    ticker = await exchange.fetchTicker(symbol)
    print(exchange.id, symbol, ticker)
    return ticker


async def fetch_tickers(id):
    exchange = getattr(ccxt, id)()
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
    await exchange.close()


asyncio.run(fetch_tickers('theocean'))
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-theocean-tickers.md`.

**Functions defined**: fetch_tickers, is_active_symbol, fetch_ticker, get_active_symbols

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 30
- Comment lines: 1
- Blank lines: 16

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

**To execute this Markdown file:**

