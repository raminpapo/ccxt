# Documentation: wiki/examples/py/fetch-ohlcv-kraken.md

## File Metadata

- **Path**: `wiki/examples/py/fetch-ohlcv-kraken.md`
- **Size**: 1,086 bytes
- **Lines**: 46
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Fetch Ohlcv Kraken](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
import asciichartpy

import ccxt  # noqa: E402
exchange = ccxt.kraken()
symbol = 'LTC/EUR'

# each ohlcv candle is a list of [ timestamp, open, high, low, close, volume ]
index = 4  # use close price from each ohlcv candle

length = 80
height = 15


def print_chart(exchange, symbol, timeframe):

    # get a list of ohlcv candles
    ohlcv = exchange.fetch_ohlcv(symbol, timeframe)

    # get the ohlCv (closing price, index == 4)
    series = [x[index] for x in ohlcv]

    # print datetime and other values
    for x in ohlcv:
        print(exchange.iso8601(x[0]), x)

    print("\n" + exchange.name + ' ' + symbol + ' ' + timeframe + ' chart:')

    # print the chart
    print("\n" + asciichartpy.plot(series[-length:], {'height': height}))  # print the chart

    last = ohlcv[len(ohlcv) - 1][index]  # last closing price
    return last


last = print_chart(exchange, symbol, '1m')
print("\n" + exchange.name + ' last price: ' + str(last) + "\n")  # print last closing price
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/fetch-ohlcv-kraken.md`.

**Functions defined**: print_chart

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 46
- Code lines: 23
- Comment lines: 6
- Blank lines: 17

### Main Components

**Functions** (1):
- `print_chart()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

