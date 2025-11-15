# Documentation: wiki/examples/py/async-macd.md

## File Metadata

- **Path**: `wiki/examples/py/async-macd.md`
- **Size**: 1,325 bytes
- **Lines**: 52
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Async Macd](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

from asyncio import gather, run
import pandas_ta as ta
import pandas as pd
import os
import sys


import ccxt.async_support as ccxt  # noqa: E402
print('CCXT Version:', ccxt.__version__)

async def run_ohlcv_loop(exchange, symbol, timeframe, limit):
    since = None
    fast = 12
    slow = 26
    signal = 9
    while True:
        try:
            ohlcv = await exchange.fetch_ohlcv(symbol, timeframe, since, limit)
            if len(ohlcv):
                df = pd.DataFrame(ohlcv, columns=['time', 'open', 'high', 'low', 'close', 'volume'])

                macd = df.ta.macd(fast=fast, slow=slow, signal=signal)
                df = pd.concat([df, macd], axis=1)
                print('----------------------------------------------------------')
                print(exchange.iso8601(exchange.milliseconds()), symbol, timeframe)
                print(df[-signal:])
        except Exception as e:
            print(type(e).__name__, str(e))


async def main():
    exchange = ccxt.binance()
    timeframe = '1m'
    limit = 50
    symbols = [
        'BTC/USDT',
        'ETH/USDT',
    ]
    loops = [run_ohlcv_loop(exchange, symbol, timeframe, limit) for symbol in symbols]
    await gather(*loops)
    await exchange.close()


run(main())
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/async-macd.md`.

**Functions defined**: main, run_ohlcv_loop

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 52
- Code lines: 39
- Comment lines: 1
- Blank lines: 12

### Main Components

**Functions** (2):
- `main()`
- `run_ohlcv_loop()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

