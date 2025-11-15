# Documentation: examples/ccxt.pro/py/binance-futures-watch-balance.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/binance-futures-watch-balance.py`
- **Size**: 1,050 bytes
- **Lines**: 40
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import ccxt
import ccxt.pro
import asyncio

from pprint import pprint

loop = asyncio.get_event_loop()


async def print_balance(exchange, market_type):
    while True:
        try:
            balance = await exchange.watch_balance({'type': market_type})
            pprint(balance)
            print('balance of ' + market_type, balance)
            print(exchange.options[market_type])
        except ccxt.BaseError as e:
            print(type(e), e)
        except Exception as e:
            print(type(e), e)


async def main():
    exchange = ccxt.pro.binance({
        "apiKey": "",
        "secret": "",
        'enableRateLimit': True,
        'newUpdates': True,
    })
    # you must make an order a transfer first to the websocket to send updates
    asyncio.ensure_future(print_balance(exchange, 'future'))
    asyncio.ensure_future(print_balance(exchange, 'delivery'))  # inverse futures settled in BTC
    asyncio.ensure_future(print_balance(exchange, 'spot'))


asyncio.run(main())
asyncio.ensure_future(main())
loop.run_forever()


```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/binance-futures-watch-balance.py`.

**Functions defined**: main, print_balance

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 40
- Code lines: 29
- Comment lines: 1
- Blank lines: 10

### Main Components

**Functions** (2):
- `main()`
- `print_balance()`



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
python examples/ccxt.pro/py/binance-futures-watch-balance.py
```

