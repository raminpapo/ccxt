# Documentation: examples/py/async-basic-callchain.py

## File Metadata

- **Path**: `examples/py/async-basic-callchain.py`
- **Size**: 2,042 bytes
- **Lines**: 78
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


async def run_all_exchanges(exchange_ids):
    results = {}

    for exchange_id in exchange_ids:

        exchange = getattr(ccxt, exchange_id)({
            'options': {
                'useWebapiForFetchingFees': False,
            }
        })

        symbol = 'ETH/BTC'
        print('Exchange:', exchange_id)

        print(exchange_id, 'symbols:')
        markets = await load_markets(exchange, symbol)  # ←----------- STEP 1
        print(list(markets.keys()))

        print(symbol, 'ticker:')
        ticker = await fetch_ticker(exchange, symbol)  # ←------------ STEP 2
        print(ticker)

        print(symbol, 'orderbook:')
        orderbook = await fetch_orderbook(exchange, symbol)  # ←------ STEP 3
        print(orderbook)

        await exchange.close()  # ←----------- LAST STEP GOES AFTER ALL CALLS

        results[exchange_id] = ticker

    return results


async def load_markets(exchange, symbol):
    try:
        result = await exchange.load_markets()
        return result
    except ccxt.BaseError as e:
        print(type(e).__name__, str(e), str(e.args))
        raise e


async def fetch_ticker(exchange, symbol):
    try:
        result = await exchange.fetch_ticker(symbol)
        return result
    except ccxt.BaseError as e:
        print(type(e).__name__, str(e), str(e.args))
        raise e


async def fetch_orderbook(exchange, symbol):
    try:
        result = await exchange.fetch_order_book(symbol)
        return result
    except ccxt.BaseError as e:
        print(type(e).__name__, str(e), str(e.args))
        raise e


if __name__ == '__main__':
    exchange_ids = ['bitfinex', 'okex', 'exmo']
    exchanges = []
    results = asyncio.run(run_all_exchanges(exchange_ids))
    print([(exchange_id, ticker) for exchange_id, ticker in results.items()])

```

## High-Level Overview

This is a Python file located at `examples/py/async-basic-callchain.py`.

**Functions defined**: run_all_exchanges, fetch_ticker, fetch_orderbook, load_markets

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 78
- Code lines: 54
- Comment lines: 1
- Blank lines: 23

### Main Components

**Functions** (4):
- `fetch_orderbook()`
- `fetch_ticker()`
- `load_markets()`
- `run_all_exchanges()`



## Usage Examples

### Main execution block:

```python
exchange_ids = ['bitfinex', 'okex', 'exmo']
    exchanges = []
    results = asyncio.run(run_all_exchanges(exchange_ids))
    print([(exchange_id, ticker) for exchange_id, ticker in results.items()])
```



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/async-basic-callchain.py
```

