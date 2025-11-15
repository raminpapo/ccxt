# Documentation: wiki/examples/py/bybit-positions.md

## File Metadata

- **Path**: `wiki/examples/py/bybit-positions.md`
- **Size**: 928 bytes
- **Lines**: 36
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Bybit Positions](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


import ccxt  # noqa: E402

from pprint import pprint

print('CCXT Version:', ccxt.__version__)

exchange = ccxt.bybit ({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})

markets = exchange.load_markets() # https://github.com/ccxt/ccxt/wiki/Manual#loading-markets

exchange.verbose = True  # uncomment for debugging
symbol = 'BTC/USDT:USDT'  # https://github.com/ccxt/ccxt/wiki/Manual#contract-naming-conventions
market = exchange.market(symbol)
params = {'subType':'linear' if market['linear'] else 'inverse'}
linear_positions = exchange.fetch_positions([ symbol ], params)
pprint(linear_positions)
symbol = 'BTC/USD:BTC'
market = exchange.market(symbol)
params = {'subType':'linear' if market['linear'] else 'inverse'}
inverse_positions = exchange.fetch_positions([ symbol ], params)
pprint(inverse_positions)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/bybit-positions.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 24
- Comment lines: 1
- Blank lines: 11

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

