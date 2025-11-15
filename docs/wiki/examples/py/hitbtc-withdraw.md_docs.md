# Documentation: wiki/examples/py/hitbtc-withdraw.md

## File Metadata

- **Path**: `wiki/examples/py/hitbtc-withdraw.md`
- **Size**: 924 bytes
- **Lines**: 47
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Hitbtc Withdraw](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

from pprint import pprint

import os
import sys


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/hitbtc-withdraw.md`.

**Functions defined**: get_positive_accounts

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 28
- Comment lines: 1
- Blank lines: 18

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

**To execute this Markdown file:**

