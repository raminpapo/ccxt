# Documentation: wiki/examples/py/coinone-fetch-tickers.md

## File Metadata

- **Path**: `wiki/examples/py/coinone-fetch-tickers.md`
- **Size**: 509 bytes
- **Lines**: 31
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Coinone Fetch Tickers](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint


import ccxt  # noqa: E402

exchange = ccxt.coinone({
    # 'verbose': True,  # uncomment for verbose output
})

# fetch all
tickers = exchange.fetch_tickers()
for symbol, ticker in tickers.items():
    print(ticker)

print("\n")

# fetch one by one
markets = exchange.load_markets()
for symbol in markets.keys():
    ticker = exchange.fetch_ticker(symbol)
    print(ticker)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/coinone-fetch-tickers.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 31
- Code lines: 17
- Comment lines: 4
- Blank lines: 10

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

