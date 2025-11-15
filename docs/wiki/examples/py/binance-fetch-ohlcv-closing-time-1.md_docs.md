# Documentation: wiki/examples/py/binance-fetch-ohlcv-closing-time-1.md

## File Metadata

- **Path**: `wiki/examples/py/binance-fetch-ohlcv-closing-time-1.md`
- **Size**: 518 bytes
- **Lines**: 23
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Binance Fetch Ohlcv Closing Time 1](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys

import ccxt  # noqa: E402


exchange = ccxt.binance()
symbol = 'BTC/USDT'
timeframe = '1h'

timeframe_duration_in_seconds = exchange.parse_timeframe(timeframe)
timeframe_duration_in_milliseconds = timeframe_duration_in_seconds * 1000
ohlcvs = exchange.fetch_ohlcv(symbol, timeframe)
for ohlcv in ohlcvs:
    print([exchange.iso8601(ohlcv[0] + timeframe_duration_in_milliseconds - 1)] + ohlcv[1:])
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/binance-fetch-ohlcv-closing-time-1.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 14
- Comment lines: 1
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

