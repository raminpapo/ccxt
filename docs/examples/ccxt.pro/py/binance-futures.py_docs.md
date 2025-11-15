# Documentation: examples/ccxt.pro/py/binance-futures.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/binance-futures.py`
- **Size**: 745 bytes
- **Lines**: 28
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import ccxt.pro as ccxt
from asyncio import run

print('CCXT Version:', ccxt.__version__)

async def main():
    exchange = ccxt.pro.binance({
        'options': {
            'defaultType': 'future',  # spot, margin, future, delivery
        },
    })
    # or
    # exchange = ccxt.pro.binanceusdm()
    # or
    # exchange = ccxt.pro.binancecoinm()
    symbol = 'BTC/USDT'
    while True:
        try:
            orderbook = await exchange.watch_order_book(symbol)
            print(exchange.iso8601(exchange.milliseconds()), exchange.id, symbol, 'ask:', orderbook['asks'][0], 'bid:', orderbook['bids'][0])
        except Exception as e:
            print(type(e).__name__, str(e))
            break
    await exchange.close()


run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/binance-futures.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 19
- Comment lines: 4
- Blank lines: 5

### Main Components

**Functions** (1):
- `main()`



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
python examples/ccxt.pro/py/binance-futures.py
```

