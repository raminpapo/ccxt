# Documentation: wiki/examples/py/gateio-fetch-ohlcv-pagination.md

## File Metadata

- **Path**: `wiki/examples/py/gateio-fetch-ohlcv-pagination.md`
- **Size**: 1,377 bytes
- **Lines**: 48
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Gateio Fetch Ohlcv Pagination](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


import ccxt  # noqa: E402


def table(values):
    first = values[0]
    keys = list(first.keys()) if isinstance(first, dict) else range(0, len(first))
    widths = [max([len(str(v[k])) for v in values]) for k in keys]
    string = ' | '.join(['{:<' + str(w) + '}' for w in widths])
    return "\n".join([string.format(*[str(v[k]) for k in keys]) for v in values])


def main():
    exchange = ccxt.gateio()
    markets = exchange.load_markets()
    # exchange.verbose = True  # uncomment for debugging purposes if necessary
    since = exchange.parse8601('2022-01-01T00:00:00Z')
    symbol = 'BTC/USDT'
    timeframe = '1h'
    all_ohlcvs = []
    while True:
        try:
            ohlcvs = exchange.fetch_ohlcv(symbol, timeframe, since)
            all_ohlcvs += ohlcvs
            if len(ohlcvs):
                print('Fetched', len(ohlcvs), symbol, timeframe, 'candles from', exchange.iso8601(ohlcvs[0][0]))
                since = ohlcvs[-1][0] + 1
            else:
                break
        except Exception as e:
            print(type(e).__name__, str(e))
    print('Fetched', len(all_ohlcvs), symbol, timeframe, 'candles in total')
    if len(all_ohlcvs):
        print(table([[exchange.iso8601(o[0])] + o[1:] for o in all_ohlcvs]))


main()
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/gateio-fetch-ohlcv-pagination.md`.

**Functions defined**: main, table

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 48
- Code lines: 34
- Comment lines: 2
- Blank lines: 12

### Main Components

**Functions** (2):
- `main()`
- `table()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

