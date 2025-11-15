# Documentation: examples/py/latoken-example.py

## File Metadata

- **Path**: `examples/py/latoken-example.py`
- **Size**: 3,803 bytes
- **Lines**: 115
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt  # noqa: E402


def table(values):
    first = values[0]
    keys = list(first.keys()) if isinstance(first, dict) else range(0, len(first))
    widths = [max([len(str(v[k])) for v in values]) for k in keys]
    string = ' | '.join(['{:<' + str(w) + '}' for w in widths])
    return "\n".join([string.format(*[str(v[k]) for k in keys]) for v in values])


symbol = 'BTC/USDT'

exchange = ccxt.latoken ({
    # 'verbose': True,  # uncomment for debugging purposes
    # uncomment and change for your keys to enable private calls
    # 'apiKey': 'YOUR_API_KEY',
    # 'secret': 'YOUR_API_SECRET',
})

exchange.load_markets()

print('-------------------------------------------------------------------')

print(exchange.id, 'has:')
pprint(exchange.has)

# public API

print('-------------------------------------------------------------------')

markets = exchange.markets.values()
print('Loaded', len(markets), exchange.id, 'markets:')
print(table([exchange.omit(x, ['info', 'limits', 'precision']) for x in markets]))

print('-------------------------------------------------------------------')

currencies = exchange.currencies.values()
print('Loaded', len(currencies), exchange.id, 'currencies:')
print(table([exchange.omit(x, ['info', 'limits']) for x in currencies]))

print('-------------------------------------------------------------------')

time = exchange.fetch_time()
print('Exchange time:', exchange.iso8601(time))

print('-------------------------------------------------------------------')

ticker = exchange.fetch_ticker(symbol)
pprint(ticker)

print('-------------------------------------------------------------------')

tickers = exchange.fetch_tickers()
tickers = tickers.values()
print(table([exchange.omit(x, ['info', 'bid', 'ask', 'bidVolume', 'askVolume', 'timestamp']) for x in tickers]))

print('-------------------------------------------------------------------')

orderbook = exchange.fetch_order_book(symbol)
pprint(orderbook)

print('-------------------------------------------------------------------')

trades = exchange.fetch_trades(symbol)
print(table([exchange.omit(x, ['info', 'timestamp']) for x in trades]))

print('-------------------------------------------------------------------')

# private API

if exchange.check_required_credentials(False):

    balance = exchange.fetch_balance()
    pprint(exchange.omit(balance, ['info']))

    print('-------------------------------------------------------------------')

    order = exchange.create_order(symbol, 'limit', 'buy', 0.001, 10000)
    pprint(order)

    print('-------------------------------------------------------------------')

    open_orders = exchange.fetch_open_orders(symbol)
    print(table([exchange.omit(x, ['info', 'timestamp']) for x in open_orders]))

    print('-------------------------------------------------------------------')

    canceled = exchange.cancel_order(order['id'], order['symbol'])
    pprint(canceled)

    print('-------------------------------------------------------------------')

    closed_orders = exchange.fetch_closed_orders(symbol)
    print(table([exchange.omit(x, ['info', 'timestamp']) for x in closed_orders]))

    print('-------------------------------------------------------------------')

    canceled_orders = exchange.fetch_canceled_orders (symbol)
    print(table([exchange.omit(x, ['info', 'timestamp']) for x in canceled_orders]))

    print('-------------------------------------------------------------------')

    my_trades = exchange.fetch_my_trades (symbol)
    print(table([exchange.omit(x, ['info', 'timestamp']) for x in my_trades]))

```

## High-Level Overview

This is a Python file located at `examples/py/latoken-example.py`.

**Functions defined**: table

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 115
- Code lines: 65
- Comment lines: 7
- Blank lines: 43

### Main Components

**Functions** (1):
- `table()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/latoken-example.py
```

