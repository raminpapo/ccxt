# Documentation: wiki/examples/py/normalize-sparse-candle-timestamps.md

## File Metadata

- **Path**: `wiki/examples/py/normalize-sparse-candle-timestamps.md`
- **Size**: 628 bytes
- **Lines**: 36
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Normalize Sparse Candle Timestamps](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint


import ccxt  # noqa: E402

exchange = ccxt.binance()

symbol = 'ETH/BTC'
timeframe = '1h'

candles = exchange.fetch_ohlcv(symbol, timeframe)

# timeframe duration in seconds
duration = exchange.parse_timeframe(timeframe)

# timeframe duration in milliseconds
duration *= 1000

pprint([[
    exchange.iso8601(int(round(candle[0] / duration)) * duration),
    candle[1],  # o
    candle[2],  # h
    candle[3],  # l
    candle[4],  # c
    candle[5]   # v
] for candle in candles])
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/normalize-sparse-candle-timestamps.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 36
- Code lines: 21
- Comment lines: 3
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

