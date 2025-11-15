# Documentation: examples/ccxt.pro/py/okx-bbo-tbt.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/okx-bbo-tbt.py`
- **Size**: 1,227 bytes
- **Lines**: 37
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import ccxt.pro
from asyncio import run


print('CCXT Pro version', ccxt.pro.__version__)


async def main():
    exchange = ccxt.pro.okx({
        'options': {
            'watchOrderBook': {
                'depth': 'bbo-tbt',  # tick-by-tick best bidask
            },
        },
    })
    markets = await exchange.load_markets()
    # exchange.verbose = True  # uncomment for debugging purposes if necessary
    symbol = 'BTC/USDT'
    while True:
        try:
            # -----------------------------------------------------------------
            # use this:
            # orderbook = await exchange.watch_order_book(symbol)
            # print(orderbook['datetime'], symbol, orderbook['asks'][0], orderbook['bids'][0])
            # -----------------------------------------------------------------
            # or this:
            ticker = await exchange.watch_ticker(symbol)
            print(ticker['datetime'], symbol, [ticker['ask'], ticker['askVolume']], [ticker['bid'], ticker['bidVolume']])
            # -----------------------------------------------------------------
        except Exception as e:
            print(type(e).__name__, str(e))
            break
    await exchange.close()


run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/okx-bbo-tbt.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 22
- Comment lines: 8
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
python examples/ccxt.pro/py/okx-bbo-tbt.py
```

