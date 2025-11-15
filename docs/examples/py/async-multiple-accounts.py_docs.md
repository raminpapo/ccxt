# Documentation: examples/py/async-multiple-accounts.py

## File Metadata

- **Path**: `examples/py/async-multiple-accounts.py`
- **Size**: 1,064 bytes
- **Lines**: 34
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


async def fetch_balance_n_times(code, account, n):
    exchange_class = getattr(ccxt, account['exchange_id'])
    exchange = exchange_class(account['params'])
    for i in range(0, n):
        balance = await exchange.fetch_balance()
        print(exchange.id, code, 'balance:', balance[code])
    await exchange.close()


async def test():
    n = 10  # fetch 10 times
    code = 'BTC'
    accounts = [
        {'exchange_id': 'binance', 'params': {'id': 'Binance1', 'apiKey': 'YOUR_API_KEY_1', 'secret': 'YOUR_API_SECRET_1'}},
        {'exchange_id': 'binance', 'params': {'id': 'Binance2', 'apiKey': 'YOUR_API_KEY_2', 'secret': 'YOUR_API_SECRET_2'}},
    ]
    coroutines = [fetch_balance_n_times(code, account, n) for account in accounts]
    await asyncio.gather(*coroutines)

if __name__ == '__main__':
    asyncio.run(test())

```

## High-Level Overview

This is a Python file located at `examples/py/async-multiple-accounts.py`.

**Functions defined**: test, fetch_balance_n_times

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 24
- Comment lines: 1
- Blank lines: 9

### Main Components

**Functions** (2):
- `fetch_balance_n_times()`
- `test()`



## Usage Examples

### Main execution block:

```python
asyncio.run(test())
```



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/async-multiple-accounts.py
```

