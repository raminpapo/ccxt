# Documentation: examples/ccxt.pro/py/okex-watch-margin-balance-with-params.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/okex-watch-margin-balance-with-params.py`
- **Size**: 1,079 bytes
- **Lines**: 36
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import asyncio
import ccxt.pro as ccxt
from pprint import pprint


async def main():
    exchange = ccxt.pro.okex({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
        # okex requires this: https://github.com/ccxt/ccxt/wiki/Manual#authentication
        'password': 'YOUR_API_PASSWORD',
        # comment it out if you don't want debug output
        # this is for the demo purpose only (to show the communication)
        'verbose': True,
    })
    while True:
        try:
            balance = await exchange.watch_balance({
                # okex watch_balance requires a symbol or an instrument_id
                'symbol': 'BTC/USDT',
                'type': 'margin',
            })
            # it will print the balance update when the balance changes
            # if the balance remains unchanged the exchange will not send it
            pprint(balance)
        except Exception as e:
            print('watch_balance() failed')
            print(e)
            break
    await exchange.close()


asyncio.run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/okex-watch-margin-balance-with-params.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 23
- Comment lines: 7
- Blank lines: 6

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
python examples/ccxt.pro/py/okex-watch-margin-balance-with-params.py
```

