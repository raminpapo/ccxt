# Documentation: wiki/examples/py/bittrex-fetch-closed-orders-history.md

## File Metadata

- **Path**: `wiki/examples/py/bittrex-fetch-closed-orders-history.md`
- **Size**: 1,744 bytes
- **Lines**: 77
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Bittrex Fetch Closed Orders History](./examples/py/)


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


exchange = ccxt.bittrex({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_API_SECRET',
})

exchange.load_markets()

symbol = 'ETH/BTC'
market = exchange.markets[symbol]
starting_date = '2017-01-01T00:00:00'
now = exchange.milliseconds()

print("\nFetching history for:", symbol, "\n")

all_orders = []
since = exchange.parse8601(starting_date)

while since < now:

    try:

        print('Fetching history for', symbol, 'since', exchange.iso8601(since))
        orders = exchange.fetch_closed_orders(symbol, since)
        print('Fetched', len(orders), 'orders')

        all_orders = all_orders + orders

        if len(orders):

            last_order = orders[-1]
            since = last_order['timestamp'] + 1

        else:

            break  # no more orders left for this symbol, move to next one

    except Exception as e:

            print(e)


# omit the following keys for a compact table output
# otherwise it won't fit into the screen width
omitted_keys = [
    'info',
    'timestamp',
    'lastTradeTimestamp',
    'fee',
]

print(table([exchange.omit(order, omitted_keys) for order in all_orders]))
print('Fetched', len(all_orders), symbol, 'orders in total')

# do whatever you want to do with them, calculate profit loss, etc...
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/bittrex-fetch-closed-orders-history.md`.

**Functions defined**: table

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 77
- Code lines: 45
- Comment lines: 4
- Blank lines: 28

### Main Components

**Functions** (1):
- `table()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

