# Documentation: examples/ccxt.pro/py/binance-watch-order-book-individual-updates.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/binance-watch-order-book-individual-updates.py`
- **Size**: 1,138 bytes
- **Lines**: 35
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

from asyncio import run
import ccxt.pro as ccxt


class MyBinance(ccxt.binance):
    def handle_order_book_message(self, client, message, orderbook):
        asks = self.safe_value(message, 'a', [])
        bids = self.safe_value(message, 'b', [])
        # printing high-frequency updates is a resource-heavy task
        # this print statement is here just to demonstrate the work of it
        # replace it with you logic for processing individual updates
        print('Updates:', {
            'asks': asks,
            'bids': bids,
        })
        return super(MyBinance, self).handle_order_book_message(client, message, orderbook);

async def main():
    exchange = MyBinance()
    symbol = 'BTC/USDT'
    print('Watching', exchange.id, symbol)
    while True:
        try:
            orderbook = await exchange.watch_order_book(symbol)
        except Exception as e:
            print(str(e))
            # raise e  # uncomment to break all loops in case of an error in any one of them
            # break  # you can also break just this one loop if it fails
    await exchange.close()


run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/binance-watch-order-book-individual-updates.py`.

**Classes defined**: MyBinance

**Functions defined**: main, handle_order_book_message

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 22
- Comment lines: 6
- Blank lines: 7

### Main Components

**Classes** (1):
- `MyBinance`

**Functions** (2):
- `handle_order_book_message()`
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
python examples/ccxt.pro/py/binance-watch-order-book-individual-updates.py
```

