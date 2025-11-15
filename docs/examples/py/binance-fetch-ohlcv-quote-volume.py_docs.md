# Documentation: examples/py/binance-fetch-ohlcv-quote-volume.py

## File Metadata

- **Path**: `examples/py/binance-fetch-ohlcv-quote-volume.py`
- **Size**: 1,718 bytes
- **Lines**: 52
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt  # noqa: E402


def table(values):
    first = values[0]
    keys = list(first.keys()) if isinstance(first, dict) else range(0, len(first))
    widths = [max([len(str(v[k])) for v in values]) for k in keys]
    string = ' | '.join(['{:<' + str(w) + '}' for w in widths])
    return "\n".join([string.format(*[str(v[k]) for k in keys]) for v in values])


class Binance(ccxt.binance):
    def parse_ohlcv(self, ohlcv, market=None):
        #
        #     [
        #         1591478520000,  # open time
        #         "0.02501300",   # open
        #         "0.02501800",   # high
        #         "0.02500000",   # low
        #         "0.02500000",   # close
        #         "22.19000000",  # volume
        #         1591478579999,  # close time
        #         "0.55490906",   # quote asset volume
        #         40,             # number of trades
        #         "10.92900000",  # taker buy base asset volume
        #         "0.27336462",   # taker buy quote asset volume
        #         "0"             # ignore
        #     ]
        #
        return [
            self.safe_integer(ohlcv, 0),
            self.safe_number(ohlcv, 1),
            self.safe_number(ohlcv, 2),
            self.safe_number(ohlcv, 3),
            self.safe_number(ohlcv, 4),
            self.safe_number(ohlcv, 7),  # << here
        ]

exchange = Binance()
markets = exchange.load_markets()
# exchange.verbose = True  # uncomment for debugging purposes if necessary
ohlcv = exchange.fetch_ohlcv('BTC/USDT', '1h')
print(table(ohlcv))

```

## High-Level Overview

This is a Python file located at `examples/py/binance-fetch-ohlcv-quote-volume.py`.

**Classes defined**: Binance

**Functions defined**: parse_ohlcv, table

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 52
- Code lines: 25
- Comment lines: 18
- Blank lines: 9

### Main Components

**Classes** (1):
- `Binance`

**Functions** (2):
- `parse_ohlcv()`
- `table()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/binance-fetch-ohlcv-quote-volume.py
```

