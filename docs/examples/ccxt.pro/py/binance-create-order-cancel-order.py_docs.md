# Documentation: examples/ccxt.pro/py/binance-create-order-cancel-order.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/binance-create-order-cancel-order.py`
- **Size**: 713 bytes
- **Lines**: 35
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import ccxt.pro
from pprint import pprint
from asyncio import run


print('CCXT Version:', ccxt.__version__)


async def main():
    exchange = ccxt.pro.binance({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
    })

    markets = await exchange.load_markets()

    # exchange.verbose = True  # uncomment for debugging purposes if necessary

    symbol = 'ETH/BTC'
    type = 'limit'  # or 'market'
    side = 'sell'  # or 'buy'
    amount = 1.0
    price = 0.060154  # or None

    order = await exchange.create_order(symbol, type, side, amount, price)
    canceled = await exchange.cancel_order(order['id'], order['symbol'])

    pprint(canceled)

    await exchange.close()


run(main())


```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/binance-create-order-cancel-order.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 20
- Comment lines: 1
- Blank lines: 14

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
python examples/ccxt.pro/py/binance-create-order-cancel-order.py
```

