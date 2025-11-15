# Documentation: wiki/examples/py/poloniex-fetch-trades-with-pagination-to-csv.md

## File Metadata

- **Path**: `wiki/examples/py/poloniex-fetch-trades-with-pagination-to-csv.md`
- **Size**: 1,664 bytes
- **Lines**: 55
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Poloniex Fetch Trades With Pagination To Csv](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
import pandas as pd


import ccxt  # noqa: E402

exchange = ccxt.poloniex()
exchange.load_markets()

# Poloniex will only serve one year of data into the past

symbol = 'BTC/USDT'
before = exchange.milliseconds()
previous_length = 0
all_trades = {}

while True:
    try:
        print('---------------------------------------------------------------')
        print('Fetching trades before', exchange.iso8601(before))
        params = {
            'end': int(before / 1000)  # end param must be in seconds
        }
        trades = exchange.fetch_trades(symbol, None, None, params)
        trades_by_id = exchange.index_by(trades, 'id')
        before = trades[0]['timestamp']
        all_trades = exchange.extend(all_trades, trades_by_id)
        total_length = len(all_trades.keys())
        print('Fetched', total_length, 'trades in total')
        if total_length == previous_length:
            break
        previous_length = total_length
    except ccxt.NetworkError as e:
        print(e)  # retry on next iteration
    except ccxt.ExchangeError as e:
        print(e)
        break

all_trades = exchange.sort_by(all_trades.values(), 'id')
print('Fetched', len(all_trades), 'trades since', all_trades[0]['datetime'], 'till', all_trades[-1]['datetime'])

# omitted_keys = ['fee', 'info']
# all_trades = [exchange.omit(trade, omitted_keys) for trade in all_trades]
# path_to_your_csv_file = 'trades.csv'  # change for your path here
# df = pd.DataFrame(all_trades)
# df.to_csv(path_to_your_csv_file, index=None, header=True)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/poloniex-fetch-trades-with-pagination-to-csv.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 55
- Code lines: 36
- Comment lines: 7
- Blank lines: 12

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

