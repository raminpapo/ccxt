# Documentation: examples/ccxt.pro/py/binance-watch-orderbook-watch-balance.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/binance-watch-orderbook-watch-balance.py`
- **Size**: 1,643 bytes
- **Lines**: 64
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import ccxt.pro
from asyncio import run, gather


data = {
    'orderbook': None,
    'balance': None,
}


def common_handler(exchange, symbol):
    market = exchange.market(symbol)
    base = market['base']
    quote = market['quote']
    balance = data['balance']
    orderbook = data['orderbook']
    if balance and orderbook:
        total = balance['total']
        tip = [ orderbook['asks'][0], orderbook['bids'][0] ]
        print(exchange.iso8601(exchange.milliseconds()), symbol, 'orderbook:', tip, 'balance:', total)


async def watch_order_book(exchange, symbol):
    while True:
        try:
            data['orderbook'] = await exchange.watch_order_book(symbol)
            common_handler(exchange, symbol)
        except Exception as e:
            print(type(e).__name__, str(e))
            break  # break this loop


async def watch_balance(exchange, symbol):
    while True:
        try:
            data['balance'] = await exchange.watch_balance()
            common_handler(exchange, symbol)
        except Exception as e:
            print(type(e).__name__, str(e))
            break  # break this loop


async def main():
    exchange = ccxt.pro.binance({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
    })
    await exchange.load_markets()
    symbol = 'BTC/USDT'
    while True:
        try:
            loops = [
                watch_order_book(exchange, symbol),
                watch_balance(exchange, symbol)
            ]
            await gather(*loops)
        except Exception as e:
            print(type(e).__name__, str(e))
            break
    await exchange.close()


run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/binance-watch-orderbook-watch-balance.py`.

**Functions defined**: main, watch_balance, common_handler, watch_order_book

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 64
- Code lines: 51
- Comment lines: 0
- Blank lines: 13

### Main Components

**Functions** (4):
- `common_handler()`
- `main()`
- `watch_balance()`
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
python examples/ccxt.pro/py/binance-watch-orderbook-watch-balance.py
```

