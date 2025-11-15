# Documentation: wiki/examples/py/margin-leverage-order-kraken.md

## File Metadata

- **Path**: `wiki/examples/py/margin-leverage-order-kraken.md`
- **Size**: 1,082 bytes
- **Lines**: 41
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Margin Leverage Order Kraken](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


import ccxt  # noqa: E402


kraken = ccxt.kraken({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})

kraken.load_markets()

for symbol in kraken.symbols:
    print(
        symbol,
        'Available leverage levels',
        'Buy:', kraken.markets[symbol]['info']['leverage_buy'],
        'Sell:', kraken.markets[symbol]['info']['leverage_sell']
    )

# THIS IS A KRAKEN-SPECIFIC EXAMPLE.
# THE LEVERAGE WILL NOT WORK WITH OTHER EXCHANGES THE SAME WAY.
# USE IMPLICIT METHODS FOR MARGIN/LEVERAGED ORDERS WITH OTHER EXCHANGES:
# https://github.com/ccxt/ccxt/wiki/Manual#implicit-api-methods

# with create_order all params (including the price=None) are needed!
# the extra param should be "leverage", not "leverage_sell" nor "leverage-sell"
kraken.create_order('BTC/USD', 'market', 'sell', 0.01, None, {'leverage': 3})

# or use a shorthand create_market_sell_order (no "price" param)
kraken.create_market_sell_order('BTC/USD', 0.01, {'leverage': 3})
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/margin-leverage-order-kraken.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 20
- Comment lines: 8
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

