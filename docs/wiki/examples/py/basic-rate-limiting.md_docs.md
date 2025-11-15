# Documentation: wiki/examples/py/basic-rate-limiting.md

## File Metadata

- **Path**: `wiki/examples/py/basic-rate-limiting.md`
- **Size**: 514 bytes
- **Lines**: 29
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Basic Rate Limiting](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

from pprint import pprint

import os
import sys


import ccxt  # noqa: E402


symbol = 'ETH/BTC'

exchange = ccxt.poloniex({
    'enableRateLimit': True,  # enabled by default
})

# print 10 times with appropriate delay
for i in range(0, 10):
    print('--------------------------------------------------------------------')
    ticker = exchange.fetch_ticker(symbol)
    ticker = exchange.omit(ticker, 'info')
    pprint(ticker)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/basic-rate-limiting.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 16
- Comment lines: 2
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

