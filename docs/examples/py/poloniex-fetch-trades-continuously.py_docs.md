# Documentation: examples/py/poloniex-fetch-trades-continuously.py

## File Metadata

- **Path**: `examples/py/poloniex-fetch-trades-continuously.py`
- **Size**: 1,143 bytes
- **Lines**: 37
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


exchange = ccxt.poloniex()

symbol = 'BTC/USDT'

end_time = exchange.milliseconds() + 30 * 60 * 1000

all_trades = {}

while end_time > exchange.milliseconds():
    try:
        print('---------------------------------------------------------------')
        trades = exchange.fetch_trades(symbol)
        trades_by_id = exchange.index_by(trades, 'id')
        all_trades = exchange.extend(all_trades, trades_by_id)
        total_length = len(all_trades.keys())
        time_remaining = int((end_time - exchange.milliseconds()) / 1000)
        print(time_remaining, 'seconds left, fetched', total_length, symbol, 'trades in total')
    except ccxt.NetworkError as e:
        print(e)  # retry on next iteration
    except ccxt.ExchangeError as e:
        print(e)
        break

all_trades = exchange.sort_by(all_trades.values(), 'id')
print('Fetched', len(all_trades), 'trades since', all_trades[0]['datetime'], 'till', all_trades[-1]['datetime'])

```

## High-Level Overview

This is a Python file located at `examples/py/poloniex-fetch-trades-continuously.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 25
- Comment lines: 1
- Blank lines: 11

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/poloniex-fetch-trades-continuously.py
```

