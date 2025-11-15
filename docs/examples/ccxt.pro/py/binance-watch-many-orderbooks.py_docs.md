# Documentation: examples/ccxt.pro/py/binance-watch-many-orderbooks.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/binance-watch-many-orderbooks.py`
- **Size**: 2,069 bytes
- **Lines**: 52
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import ccxt.pro as ccxt
import asyncio

orderbooks = {}

def when_orderbook_changed(exchange_spot, symbol, orderbook):
    # this is a common handler function
    # it is called when any of the orderbook is updated
    # it has access to both the orderbook that was updated
    # as well as the rest of the orderbooks
    # ...................................................................
    print('-------------------------------------------------------------')
    print('Last updated:', exchange_spot.iso8601(exchange_spot.milliseconds()))
    # ...................................................................
    # print just one orderbook here
    # print(orderbook['datetime'], symbol, orderbook['asks'][0], orderbook['bids'][0])
    # ...................................................................
    # or print all orderbooks that have been already subscribed-to
    for symbol, orderbook in orderbooks.items():
        print(orderbook['datetime'], symbol, orderbook['asks'][0], orderbook['bids'][0])


async def watch_one_orderbook(exchange_spot, symbol):
    # a call cost of 1 in the queue of subscriptions
    # means one subscription per exchange.rateLimit milliseconds
    your_delay = 1
    await exchange_spot.throttle(your_delay)
    while True:
        try:
            orderbook = await exchange_spot.watch_order_book(symbol)
            orderbooks[symbol] = orderbook
            when_orderbook_changed(exchange_spot, symbol, orderbook)
        except Exception as e:
            print(type(e).__name__, str(e))


async def watch_some_orderbooks(exchange_spot, symbol_list):
    loops = [watch_one_orderbook(exchange_spot, symbol) for symbol in symbol_list]
    # let them run, don't for all tasks cause they execute asynchronously
    # don't print here
    await asyncio.gather(*loops)


async def main():
    exchange_spot = ccxt.binance()
    await exchange_spot.load_markets()
    await watch_some_orderbooks(exchange_spot, ['ZEN/USDT', 'RUNE/USDT', 'AAVE/USDT', 'SNX/USDT'])
    await exchange_spot.close()


asyncio.run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/binance-watch-many-orderbooks.py`.

**Functions defined**: when_orderbook_changed, main, watch_some_orderbooks, watch_one_orderbook

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 52
- Code lines: 27
- Comment lines: 14
- Blank lines: 11

### Main Components

**Functions** (4):
- `main()`
- `watch_one_orderbook()`
- `watch_some_orderbooks()`
- `when_orderbook_changed()`



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
python examples/ccxt.pro/py/binance-watch-many-orderbooks.py
```

