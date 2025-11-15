# Documentation: wiki/examples/py/fetch-ohlcv-mark-index-price.md

## File Metadata

- **Path**: `wiki/examples/py/fetch-ohlcv-mark-index-price.md`
- **Size**: 713 bytes
- **Lines**: 41
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Fetch Ohlcv Mark Index Price](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint

import ccxt  # noqa: E402

print('CCXT Version:', ccxt.__version__)
exchange = ccxt.binanceusdm()

response = exchange.fetchOHLCV(
    symbol='ADA/USDT',
    timeframe='1h',
    params={"price": 'index'}
)

pprint(response)

# Convenience methods --------------------------------------------------------

markKlines = exchange.fetchMarkOHLCV(
    symbol='ADA/USDT',
    timeframe='1h',
    params={"price": 'mark'}
)

indexKlines = exchange.fetchIndexOHLCV(
    symbol='ADA/USDT',
    timeframe='1h',
    params={"price": 'mark'}
)

pprint(markKlines)
pprint(indexKlines)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/fetch-ohlcv-mark-index-price.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 27
- Comment lines: 2
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

