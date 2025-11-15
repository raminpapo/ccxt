# Documentation: wiki/examples/py/coinbase-fetch-trades.md

## File Metadata

- **Path**: `wiki/examples/py/coinbase-fetch-trades.md`
- **Size**: 613 bytes
- **Lines**: 32
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Coinbase Fetch Trades](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint


import ccxt  # noqa: E402
print('CCXT Version:', ccxt.__version__)
exchange = ccxt.coinbase({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_API_SECRET',
    # 'verbose': True,  # for debug output
})

symbol = 'BTC/USDT'
since = None  # not used by coinbase
limit = 3

try:
    trades = exchange.fetch_trades(symbol, since, limit)
    my_trades = exchange.fetch_my_trades(symbol, since, limit)
    pprint(trades)
    pprint(my_trades)
except Exception as err:
    print(err)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/coinbase-fetch-trades.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 22
- Comment lines: 2
- Blank lines: 8

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

