# Documentation: examples/py/fetch-ohlcv-kraken.py

## File Metadata

- **Path**: `examples/py/fetch-ohlcv-kraken.py`
- **Size**: 1,460 bytes
- **Lines**: 53
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys
import asciichartpy

# -----------------------------------------------------------------------------

this_folder = os.path.dirname(os.path.abspath(__file__))
root_folder = os.path.dirname(os.path.dirname(this_folder))
sys.path.append(root_folder + '/python')
sys.path.append(this_folder)

# -----------------------------------------------------------------------------

import ccxt  # noqa: E402

# -----------------------------------------------------------------------------

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

## High-Level Overview

This is a Python file located at `examples/py/fetch-ohlcv-kraken.py`.

**Functions defined**: print_chart

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 53
- Code lines: 24
- Comment lines: 9
- Blank lines: 20

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

**To execute this Python file:**

```bash
python examples/py/fetch-ohlcv-kraken.py
```

