# Documentation: examples/py/async-bitstamp-create-limit-buy-order.py

## File Metadata

- **Path**: `examples/py/async-bitstamp-create-limit-buy-order.py`
- **Size**: 1,071 bytes
- **Lines**: 47
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import asyncio
import os
import sys

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt.async_support as ccxt  # noqa: E402


async def test():

    exchange = ccxt.bitstamp({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
    })

    response = None

    try:

        await exchange.load_markets()  # force-preload markets first

        exchange.verbose = True  # this is for debugging

        symbol = 'BTC/USD'  # change for your symbol
        amount = 1.0        # change the amount
        price = 6000.00     # change the price

        try:

            response = await exchange.create_limit_buy_order(symbol, amount, price)

        except Exception as e:
            print('Failed to create order with', exchange.id, type(e).__name__, str(e))

    except Exception as e:
        print('Failed to load markets from', exchange.id, type(e).__name__, str(e))

    await exchange.close()
    return response


print(asyncio.run(test()))

```

## High-Level Overview

This is a Python file located at `examples/py/async-bitstamp-create-limit-buy-order.py`.

**Functions defined**: test

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 27
- Comment lines: 1
- Blank lines: 19

### Main Components

**Functions** (1):
- `test()`



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
python examples/py/async-bitstamp-create-limit-buy-order.py
```

