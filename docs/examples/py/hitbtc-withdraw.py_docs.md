# Documentation: examples/py/hitbtc-withdraw.py

## File Metadata

- **Path**: `examples/py/hitbtc-withdraw.py`
- **Size**: 987 bytes
- **Lines**: 44
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

from pprint import pprint

import os
import sys

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt  # noqa: E402


def get_positive_accounts(balance):
    result = {}
    currencies = list(balance.keys())
    for currency in currencies:
        if balance[currency] and balance[currency] > 0:
            result[currency] = balance[currency]
    return result


exchange = ccxt.hitbtc({
    'apiKey': "YOUR_API_KEY",
    'secret': "YOUR_SECRET",
    'enableRateLimit': True,
})


trading_balance = exchange.fetch_balance()
account_balance = exchange.fetch_balance({'type': 'account'})

pprint('Trading balance:')
pprint(get_positive_accounts(trading_balance['total']))
pprint('Account balance:')
pprint(get_positive_accounts(account_balance['total']))


withdraw = exchange.withdraw('ETH', 0.01, '0x811DCfeb6dC0b9ed825808B6B060Ca469b83fB81')


pprint('Withdraw:')
pprint(withdraw)

```

## High-Level Overview

This is a Python file located at `examples/py/hitbtc-withdraw.py`.

**Functions defined**: get_positive_accounts

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 27
- Comment lines: 1
- Blank lines: 16

### Main Components

**Functions** (1):
- `get_positive_accounts()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/hitbtc-withdraw.py
```

