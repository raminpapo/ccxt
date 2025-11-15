# Documentation: wiki/examples/py/bitmex-order-value.md

## File Metadata

- **Path**: `wiki/examples/py/bitmex-order-value.md`
- **Size**: 1,407 bytes
- **Lines**: 48
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Bitmex Order Value](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


import ccxt  # noqa: E402


exchange = ccxt.bitmex()

markets = exchange.load_markets()
symbol = 'XBTU20'
market = exchange.market(symbol)

units = {
    'XBT':  { 'decimals': 4, 'multiplier': 1, 'name': 'bitcoin' },
    'mXBT': { 'decimals': 3, 'multiplier': 1000, 'name': 'milli-bitcoin'  },
    'μXBT': { 'decimals': 1, 'multiplier': 1000000, 'name': 'micro-bitcoin' },
    'XBt':  { 'decimals': 0, 'multiplier': 100000000, 'name': 'satoshi' },
}

# the following calculation depends on contract specifications
# one XBTU20 contract = 1 USD in Bitcoin

num_contracts = 1

while True:
    try:
        ticker = exchange.fetch_ticker(symbol)
        last_price = ticker['last']
        value = num_contracts / last_price
        print('---------------------------------------------------------------')
        print(exchange.iso8601(exchange.milliseconds()))
        for unit in units:
            multiplier = units[unit]['multiplier']
            decimals = units[unit]['decimals']
            name = units[unit]['name']
            rounded_value = exchange.decimal_to_precision(value * multiplier, ccxt.ROUND, decimals)  # alternatively, use ccxt.TRUNCATE here
            print(num_contracts, symbol, 'contracts =', rounded_value, unit, '(' + name + ')')
    except Exception as e:
        pass
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/bitmex-order-value.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 48
- Code lines: 32
- Comment lines: 3
- Blank lines: 13

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

