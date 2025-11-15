# Documentation: wiki/examples/py/bitget-perpetual-futures-swaps.md

## File Metadata

- **Path**: `wiki/examples/py/bitget-perpetual-futures-swaps.md`
- **Size**: 1,279 bytes
- **Lines**: 56
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Bitget Perpetual Futures Swaps](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


import ccxt  # noqa: E402


def main():
    exchange = ccxt.bitget({
        'apiKey': 'YOUR_API_KEY',
        'secret': 'YOUR_SECRET',
        'password': 'YOUR_API_PASSWORD',
        'options': {
            'defaultType': 'swap',
        }
    })

    try:

        markets = exchange.load_markets()

        # exchange.verbose = True  # uncomment for debugging purposes if necessary

        # fetching balance
        balance = exchange.fetch_balance()
        print(balance['total'])

        # placing a limit order
        symbol = 'ETH/USDT:USDT'
        type = 'limit'
        side = 'buy'
        amount = 1  # how many contracts to buy or sell, integer number of contracts
        price = 3000
        order = exchange.create_order(symbol, type, side, amount, price)
        print(order)

        # placing a market order
        symbol = 'ETH/USDT:USDT'
        type = 'market'
        side = 'sell'
        amount = 1  # how many contracts to buy or sell, integer number of contracts
        order = exchange.create_order(symbol, type, side, amount)
        print(order)

    except Exception as e:
        print(type(e).__name__, str(e))


main() 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/bitget-perpetual-futures-swaps.md`.

**Functions defined**: main

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 56
- Code lines: 35
- Comment lines: 5
- Blank lines: 16

### Main Components

**Functions** (1):
- `main()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

