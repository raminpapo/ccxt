# Documentation: examples/ccxt.pro/py/one-exchange-different-streams.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/one-exchange-different-streams.py`
- **Size**: 905 bytes
- **Lines**: 36
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import ccxt.pro
import asyncio


async def watch_order_book(exchange, symbol):
    while True:
        orderbook = await exchange.watch_order_book(symbol)
        print(orderbook['datetime'], symbol, orderbook['asks'][0], orderbook['bids'][0])


async def watch_trades(exchange, symbol):
    while True:
        trades = await exchange.watch_trades(symbol)
        last = trades[-1]
        print(last['datetime'], last['price'], last['amount'])


async def main():
    exchange = ccxt.pro.bitstamp()
    await exchange.load_markets()
    symbol = 'BTC/USD'
    while True:
        try:
            loops = [
                watch_order_book(exchange, symbol),
                watch_trades(exchange, symbol)
            ]
            await asyncio.gather(*loops)
        except Exception as e:
            print(type(e).__name__, str(e))
            break
    await exchange.close()


asyncio.run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/one-exchange-different-streams.py`.

**Functions defined**: main, watch_trades, watch_order_book

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 27
- Comment lines: 0
- Blank lines: 9

### Main Components

**Functions** (3):
- `main()`
- `watch_order_book()`
- `watch_trades()`



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
python examples/ccxt.pro/py/one-exchange-different-streams.py
```

