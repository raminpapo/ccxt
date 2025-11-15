# Documentation: wiki/examples/py/binance-futures-set-leverage-implicit-api.md

## File Metadata

- **Path**: `wiki/examples/py/binance-futures-set-leverage-implicit-api.md`
- **Size**: 518 bytes
- **Lines**: 35
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Binance Futures Set Leverage Implicit Api](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


import ccxt  # noqa: E402


exchange = ccxt.binance({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
    'options': {
        'defaultType': 'future',
    }
})

exchange.load_markets()

symbol = 'ADA/USDT'
market = exchange.market(symbol)
leverage =  10

response = exchange.fapiprivate_post_leverage({
    'symbol': market['id'],
    'leverage': leverage,
})

print(response)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/binance-futures-set-leverage-implicit-api.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 35
- Code lines: 22
- Comment lines: 1
- Blank lines: 12

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

