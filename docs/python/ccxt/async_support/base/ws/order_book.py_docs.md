# Documentation: python/ccxt/async_support/base/ws/order_book.py

## File Metadata

- **Path**: `python/ccxt/async_support/base/ws/order_book.py`
- **Size**: 2,894 bytes
- **Lines**: 79
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

from ccxt.async_support.base.ws import order_book_side
from ccxt import Exchange
import sys


class OrderBook(dict):
    def __init__(self, snapshot={}, depth=None):
        self.cache = []
        depth = depth or sys.maxsize
        defaults = {
            'bids': [],
            'asks': [],
            'timestamp': None,
            'datetime': None,
            'nonce': None,
            'symbol': None,
        }
        # do not mutate snapshot
        defaults.update(snapshot)
        if not isinstance(defaults['asks'], order_book_side.OrderBookSide):
            defaults['asks'] = order_book_side.Asks(defaults['asks'], depth)
        if not isinstance(defaults['bids'], order_book_side.OrderBookSide):
            defaults['bids'] = order_book_side.Bids(defaults['bids'], depth)
        defaults['datetime'] = Exchange.iso8601(defaults.get('timestamp'))
        # merge to self
        super(OrderBook, self).__init__(defaults)

    def limit(self):
        self['asks'].limit()
        self['bids'].limit()
        return self

    def reset(self, snapshot={}):
        self['asks']._index.clear()
        self['asks'].clear()
        for ask in snapshot.get('asks', []):
            self['asks'].storeArray(ask)
        self['bids']._index.clear()
        self['bids'].clear()
        for bid in snapshot.get('bids', []):
            self['bids'].storeArray(bid)
        self['nonce'] = snapshot.get('nonce')
        self['timestamp'] = snapshot.get('timestamp')
        self['datetime'] = Exchange.iso8601(self['timestamp'])
        self['symbol'] = snapshot.get('symbol')

    def update(self, snapshot):
        nonce = snapshot.get('nonce')
        if nonce is not None and self['nonce'] is not None and nonce < self['nonce']:
            return self
        self.reset(snapshot)

# -----------------------------------------------------------------------------
# overwrites absolute volumes at price levels
# or deletes price levels based on order counts (3rd value in a bidask delta)


class CountedOrderBook(OrderBook):
    def __init__(self, snapshot={}, depth=None):
        copy = Exchange.extend(snapshot, {
            'asks': order_book_side.CountedAsks(snapshot.get('asks', []), depth),
            'bids': order_book_side.CountedBids(snapshot.get('bids', []), depth),
        })
        super(CountedOrderBook, self).__init__(copy, depth)

# -----------------------------------------------------------------------------
# indexed by order ids (3rd value in a bidask delta)


class IndexedOrderBook(OrderBook):
    def __init__(self, snapshot={}, depth=None):
        copy = Exchange.extend(snapshot, {
            'asks': order_book_side.IndexedAsks(snapshot.get('asks', []), depth),
            'bids': order_book_side.IndexedBids(snapshot.get('bids', []), depth),
        })
        super(IndexedOrderBook, self).__init__(copy, depth)

```

## High-Level Overview

This is a Python file located at `python/ccxt/async_support/base/ws/order_book.py`.

**Classes defined**: OrderBook, IndexedOrderBook, CountedOrderBook

**Functions defined**: limit, update, __init__, reset

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 79
- Code lines: 58
- Comment lines: 8
- Blank lines: 13

### Main Components

**Classes** (3):
- `CountedOrderBook`
- `IndexedOrderBook`
- `OrderBook`

**Functions** (4):
- `__init__()`
- `limit()`
- `reset()`
- `update()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Implements caching mechanisms



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/async_support/base/ws/order_book.py
```

