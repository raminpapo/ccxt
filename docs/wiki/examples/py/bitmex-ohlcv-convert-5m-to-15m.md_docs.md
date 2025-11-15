# Documentation: wiki/examples/py/bitmex-ohlcv-convert-5m-to-15m.md

## File Metadata

- **Path**: `wiki/examples/py/bitmex-ohlcv-convert-5m-to-15m.md`
- **Size**: 1,137 bytes
- **Lines**: 56
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Bitmex Ohlcv Convert 5m To 15m](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint


import ccxt  # noqa: E402


bitmex = ccxt.bitmex()

# fetch 5m OHLCV

symbol = 'BTC/USD'

ohlcv5 = bitmex.fetch_ohlcv(symbol, '5m')
ohlcv15 = []

# OHLCV key indexes

timestamp = 0
open = 1
high = 2
low = 3
close = 4
volume = 5

# convert 5m → 15m

if len(ohlcv5) > 2:
    for i in range(0, len(ohlcv5) - 2, 3):
        highs = [ohlcv5[i + j][high] for j in range(0, 3) if ohlcv5[i + j][high]]
        lows = [ohlcv5[i + j][low] for j in range(0, 3) if ohlcv5[i + j][low]]
        volumes = [ohlcv5[i + j][volume] for j in range(0, 3) if ohlcv5[i + j][volume]]
        candle = [
            ohlcv5[i + 0][timestamp],
            ohlcv5[i + 0][open],
            max(highs) if len(highs) else None,
            min(lows) if len(lows) else None,
            ohlcv5[i + 2][close],
            sum(volumes) if len(volumes) else None,
        ]
        ohlcv15.append(candle)
else:
    raise Exception('Too few 5m candles')

# do whatever you want with your 15m candles here...

pprint(ohlcv15)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/bitmex-ohlcv-convert-5m-to-15m.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 56
- Code lines: 34
- Comment lines: 5
- Blank lines: 17

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

