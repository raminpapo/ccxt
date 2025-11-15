# Documentation: examples/py/basic-chart.py

## File Metadata

- **Path**: `examples/py/basic-chart.py`
- **Size**: 1,491 bytes
- **Lines**: 52
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys

from asciichart import plot

# -----------------------------------------------------------------------------

this_folder = os.path.dirname(os.path.abspath(__file__))
root_folder = os.path.dirname(os.path.dirname(this_folder))
sys.path.append(root_folder + '/python')
sys.path.append(this_folder)

# -----------------------------------------------------------------------------

import ccxt  # noqa: E402

# -----------------------------------------------------------------------------

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

## High-Level Overview

This is a Python file located at `examples/py/basic-chart.py`.

**Functions defined**: print_chart

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 52
- Code lines: 23
- Comment lines: 8
- Blank lines: 21

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
python examples/py/basic-chart.py
```

