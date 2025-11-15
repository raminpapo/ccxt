# Documentation: wiki/examples/py/coinbase-fetch-OHLCV.md

## File Metadata

- **Path**: `wiki/examples/py/coinbase-fetch-OHLCV.md`
- **Size**: 581 bytes
- **Lines**: 32
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Coinbase Fetch Ohlcv](./examples/py/)


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
timeframe = '1m'
since = None
limit = None  # not used by coinbase

try:
    # Max 300 Candles
    candles = exchange.fetch_ohlcv(symbol, timeframe, since, limit)
    pprint(candles)
except Exception as err:
    print(err)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/coinbase-fetch-OHLCV.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 21
- Comment lines: 3
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

