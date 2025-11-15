# Documentation: wiki/examples/py/basic-chart.md

## File Metadata

- **Path**: `wiki/examples/py/basic-chart.md`
- **Size**: 1,110 bytes
- **Lines**: 45
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Basic Chart](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys

from asciichart import plot

import ccxt  # noqa: E402
kraken = ccxt.kraken()
coinbasepro = ccxt.coinbasepro()

symbol = 'BTC/USD'

# each ohlcv candle is a list of [ timestamp, open, high, low, close, volume ]
index = 4  # use close price from each ohlcv candle


def print_chart(exchange, symbol, timeframe):

    print("\n" + exchange.name + ' ' + symbol + ' ' + timeframe + ' chart:')

    # get a list of ohlcv candles
    ohlcv = exchange.fetch_ohlcv(symbol, timeframe)

    # get the ohlCv (closing price, index == 4)
    series = [x[index] for x in ohlcv]

    # print the chart
    print("\n" + plot(series[-120:], {'height': 20}))  # print the chart

    last = ohlcv[len(ohlcv) - 1][index]  # last closing price
    return last


last = print_chart(kraken, 'BTC/USD', '1h')
print("\n" + kraken.name + " ₿ = $" + str(last) + "\n")  # print last closing price

last = print_chart(coinbasepro, 'BTC/USD', '1h')
print("\n" + coinbasepro.name + " ₿ = $" + str(last) + "\n")  # print last closing price
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/basic-chart.md`.

**Functions defined**: print_chart

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 45
- Code lines: 22
- Comment lines: 5
- Blank lines: 18

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

