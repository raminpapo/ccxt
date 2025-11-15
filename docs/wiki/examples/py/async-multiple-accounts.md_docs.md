# Documentation: wiki/examples/py/async-multiple-accounts.md

## File Metadata

- **Path**: `wiki/examples/py/async-multiple-accounts.md`
- **Size**: 1,009 bytes
- **Lines**: 37
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Multiple Accounts](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import asyncio
import os
import sys


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-multiple-accounts.md`.

**Functions defined**: test, fetch_balance_n_times

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 25
- Comment lines: 1
- Blank lines: 11

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

**To execute this Markdown file:**

