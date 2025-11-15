# Documentation: examples/py/fetch-ohlcv-cex.py

## File Metadata

- **Path**: `examples/py/fetch-ohlcv-cex.py`
- **Size**: 1,348 bytes
- **Lines**: 49
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys
import asciichart

# -----------------------------------------------------------------------------

this_folder = os.path.dirname(os.path.abspath(__file__))
root_folder = os.path.dirname(os.path.dirname(this_folder))
sys.path.append(root_folder + '/python')
sys.path.append(this_folder)

# -----------------------------------------------------------------------------

import ccxt  # noqa: E402

# -----------------------------------------------------------------------------

exchange = ccxt.cex()
symbol = 'BTC/USD'

# each ohlcv candle is a list of [ timestamp, open, high, low, close, volume ]
index = 4  # use close price from each ohlcv candle

length = 80
height = 15


def print_chart(exchange, symbol, timeframe):

    print("\n" + exchange.name + ' ' + symbol + ' ' + timeframe + ' chart:')

    # get a list of ohlcv candles
    ohlcv = exchange.fetch_ohlcv(symbol, timeframe)

    # get the ohlCv (closing price, index == 4)
    series = [x[index] for x in ohlcv]

    # print the chart
    print("\n" + asciichart.plot(series[-length:], {'height': height}))  # print the chart

    last = ohlcv[len(ohlcv) - 1][index]  # last closing price
    return last


last = print_chart(exchange, symbol, '1m')
print("\n" + exchange.name + " ₿ = $" + str(last) + "\n")  # print last closing price

```

## High-Level Overview

This is a Python file located at `examples/py/fetch-ohlcv-cex.py`.

**Functions defined**: print_chart

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 49
- Code lines: 22
- Comment lines: 8
- Blank lines: 19

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
python examples/py/fetch-ohlcv-cex.py
```

