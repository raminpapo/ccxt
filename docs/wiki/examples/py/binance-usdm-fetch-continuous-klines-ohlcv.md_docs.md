# Documentation: wiki/examples/py/binance-usdm-fetch-continuous-klines-ohlcv.md

## File Metadata

- **Path**: `wiki/examples/py/binance-usdm-fetch-continuous-klines-ohlcv.md`
- **Size**: 1,273 bytes
- **Lines**: 44
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Binance Usdm Fetch Continuous Klines Ohlcv](./examples/py/)


 ```python
 
# -*- coding: utf-8 -*-

import os
import sys

import ccxt  # noqa: E402

print('CCXT Version:', ccxt.__version__)


def table(values):
    first = values[0]
    keys = list(first.keys()) if isinstance(first, dict) else range(0, len(first))
    widths = [max([len(str(v[k])) for v in values]) for k in keys]
    string = ' | '.join(['{:<' + str(w) + '}' for w in widths])
    return "\n".join([string.format(*[str(v[k]) for k in keys]) for v in values])


exchange = ccxt.binanceusdm()
try:
    exchange.load_markets()
    timeframe = '1m'
    limit = 1
    symbol = 'BTC/USDT'
    market = exchange.market(symbol)
    timeframe = '1m'
    params = {
        'pair': market['id'],
        'contractType': 'PERPETUAL',  # 'PERPETUAL', 'CURRENT_MONTH', 'NEXT_MONTH', 'CURRENT_QUARTER', 'NEXT_QUARTER'
        'interval': exchange.timeframes[timeframe],
    }
    # https://binance-docs.github.io/apidocs/futures/en/#continuous-contract-kline-candlestick-data
    ohlcvs = exchange.fapiPublic_get_continuousklines(params)
    print(table([o for o in ohlcvs]))
    print(table([[exchange.iso8601(int(o[0]))] + o[1:] for o in ohlcvs]))
except Exception as e:
    print(type(e).__name__, str(e))
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/binance-usdm-fetch-continuous-klines-ohlcv.md`.

**Functions defined**: table

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 31
- Comment lines: 2
- Blank lines: 11

### Main Components

**Functions** (1):
- `table()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

