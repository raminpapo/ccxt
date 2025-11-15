# Documentation: examples/ccxt.pro/py/bitvavo-watch-order-book.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/bitvavo-watch-order-book.py`
- **Size**: 546 bytes
- **Lines**: 24
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import ccxt.pro
from asyncio import run


print('CCXT Pro version', ccxt.pro.__version__)


async def main():
    exchange = ccxt.pro.bitvavo()
    await exchange.load_markets()
    exchange.verbose = True
    symbol = 'BTC/EUR'
    while True:
        try:
            orderbook = await exchange.watch_order_book(symbol)
            print(orderbook['nonce'], symbol, orderbook['asks'][0], orderbook['bids'][0])
        except Exception as e:
            print(type(e).__name__, str(e))
            break
    await exchange.close()


run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/bitvavo-watch-order-book.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 24
- Code lines: 17
- Comment lines: 0
- Blank lines: 7

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
python examples/ccxt.pro/py/bitvavo-watch-order-book.py
```

