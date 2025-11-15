# Documentation: examples/ccxt.pro/py/binance-reload-markets.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/binance-reload-markets.py`
- **Size**: 1,231 bytes
- **Lines**: 43
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import ccxt.pro
from asyncio import run, gather


print('CCXT Pro version', ccxt.pro.__version__)


async def watch_order_book(exchange, symbol):
    while True:
        try:
            orderbook = await exchange.watch_order_book(symbol)
            datetime = exchange.iso8601(exchange.milliseconds())
            print(datetime, orderbook['nonce'], symbol, orderbook['asks'][0], orderbook['bids'][0])
        except Exception as e:
            print(type(e).__name__, str(e))
            break


async def reload_markets(exchange, delay):
    while True:
        try:
            await exchange.sleep(delay)
            markets = await exchange.load_markets(True)
            datetime = exchange.iso8601(exchange.milliseconds())
            print(datetime, 'Markets reloaded')
        except Exception as e:
            print(type(e).__name__, str(e))
            break


async def main():
    exchange = ccxt.pro.binance()
    await exchange.load_markets()
    # exchange.verbose = True
    symbol = 'BTC/USDT'
    delay = 60000  # every minute = 60 seconds = 60000 milliseconds
    loops = [watch_order_book(exchange, symbol), reload_markets(exchange, delay)]
    await gather(*loops)
    await exchange.close()


run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/binance-reload-markets.py`.

**Functions defined**: reload_markets, main, watch_order_book

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 43
- Code lines: 31
- Comment lines: 1
- Blank lines: 11

### Main Components

**Functions** (3):
- `main()`
- `reload_markets()`
- `watch_order_book()`



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
python examples/ccxt.pro/py/binance-reload-markets.py
```

