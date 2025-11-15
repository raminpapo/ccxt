# Documentation: examples/py/fetch-ohlcv-mark-index-price.py

## File Metadata

- **Path**: `examples/py/fetch-ohlcv-mark-index-price.py`
- **Size**: 927 bytes
- **Lines**: 44
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

# -----------------------------------------------------------------------------

import ccxt  # noqa: E402

print('CCXT Version:', ccxt.__version__)

# -----------------------------------------------------------------------------

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

## High-Level Overview

This is a Python file located at `examples/py/fetch-ohlcv-mark-index-price.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 26
- Comment lines: 4
- Blank lines: 14

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/fetch-ohlcv-mark-index-price.py
```

