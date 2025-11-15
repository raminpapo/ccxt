# Documentation: examples/py/binance-fetch-ohlcv-closing-time-2.py

## File Metadata

- **Path**: `examples/py/binance-fetch-ohlcv-closing-time-2.py`
- **Size**: 1,474 bytes
- **Lines**: 55
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

class MyBinance(ccxt.binance):
    def parse_ohlcv(self, ohlcv, market=None):
        #
        #     [
        #         1591478520000,
        #         "0.02501300",
        #         "0.02501800",
        #         "0.02500000",
        #         "0.02500000",
        #         "22.19000000",
        #         1591478579999,
        #         "0.55490906",
        #         40,
        #         "10.92900000",
        #         "0.27336462",
        #         "0"
        #     ]
        #
        return [
            self.safe_integer(ohlcv, 6),
            self.safe_number(ohlcv, 1),
            self.safe_number(ohlcv, 2),
            self.safe_number(ohlcv, 3),
            self.safe_number(ohlcv, 4),
            self.safe_number(ohlcv, 5),
        ]


exchange = MyBinance()
symbol = 'BTC/USDT'
timeframe = '1h'

ohlcvs = exchange.fetch_ohlcv(symbol, timeframe)
for ohlcv in ohlcvs:
    print([exchange.iso8601(ohlcv[0])] + ohlcv[1:])

```

## High-Level Overview

This is a Python file located at `examples/py/binance-fetch-ohlcv-closing-time-2.py`.

**Classes defined**: MyBinance

**Functions defined**: parse_ohlcv

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 55
- Code lines: 24
- Comment lines: 20
- Blank lines: 11

### Main Components

**Classes** (1):
- `MyBinance`

**Functions** (1):
- `parse_ohlcv()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/binance-fetch-ohlcv-closing-time-2.py
```

