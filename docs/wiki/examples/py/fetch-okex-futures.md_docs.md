# Documentation: wiki/examples/py/fetch-okex-futures.md

## File Metadata

- **Path**: `wiki/examples/py/fetch-okex-futures.md`
- **Size**: 452 bytes
- **Lines**: 20
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Fetch Okex Futures](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
import time
import ccxt  # noqa: E402
exchange = ccxt.okex()
exchange.load_markets()
for symbol in exchange.markets:
    market = exchange.markets[symbol]
    if market['future']:
        print('----------------------------------------------------')
        print(symbol, exchange.fetchTicker(symbol))
        time.sleep(exchange.rateLimit / 1000)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/fetch-okex-futures.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 20
- Code lines: 15
- Comment lines: 1
- Blank lines: 4

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

