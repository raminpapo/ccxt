# Documentation: examples/ccxt.pro/py/phemex-cancel-all-orders.py

## File Metadata

- **Path**: `examples/ccxt.pro/py/phemex-cancel-all-orders.py`
- **Size**: 587 bytes
- **Lines**: 24
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import ccxt.pro
from asyncio import run
from pprint import pprint

print('CCXT Version:', ccxt.__version__)

async def main():
    exchange = ccxt.pro.phemex({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
    })
    markets = await exchange.load_markets()
    # exchange.verbose = True  # uncomment for debugging purposes if necessary
    try:
        symbol = 'UNI/USDT'
        response = await exchange.cancel_all_orders(symbol)
        pprint(response)
    except Exception as e:
        print(type(e).__name__, str(e))
    await exchange.close()


run(main())

```

## High-Level Overview

This is a Python file located at `examples/ccxt.pro/py/phemex-cancel-all-orders.py`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 24
- Code lines: 18
- Comment lines: 1
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
python examples/ccxt.pro/py/phemex-cancel-all-orders.py
```

