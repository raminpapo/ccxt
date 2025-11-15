# Documentation: examples/ccxt.pro/py/binance-watch-margin-balance.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/binance-watch-margin-balance.py`
- **Size**: 1,152 bytes
- **Lines**: 41
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

from asyncio import run
import ccxt.pro as ccxt
from pprint import pprint


# This example will run silent and will return your balance only when the balance is updated.

# 1. launch the example with your keys and keep it running
# 2. go to the margin trading on the website
# 3. place a margin order on a spot market
# 4. see your balance updated in the example


async def main():
    exchange = ccxt.pro.binance({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
        'options': {
            'defaultType': 'margin',
        },
        # comment it out if you don't want debug output
        # this is for the demo purpose only (to show the communication)
        'verbose': True,
    })
    while True:
        try:
            balance = await exchange.watch_balance()
            # it will print the balance update when the balance changes
            # if the balance remains unchanged the exchange will not send it
            pprint(balance)
        except Exception as e:
            print('watch_balance() failed')
            print(e)
            break
    await exchange.close()


run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/binance-watch-margin-balance.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 22
- Comment lines: 10
- Blank lines: 9

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
python examples/ccxt.pro/py/binance-watch-margin-balance.py
```

