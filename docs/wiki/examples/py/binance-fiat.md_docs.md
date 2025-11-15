# Documentation: wiki/examples/py/binance-fiat.md

## File Metadata

- **Path**: `wiki/examples/py/binance-fiat.md`
- **Size**: 573 bytes
- **Lines**: 28
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Binance Fiat](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


import ccxt  # noqa: E402


exchange = ccxt.binance({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})

markets = exchange.load_markets()

fiat_currencies = [currency['code'] for currency in exchange.currencies.values() if currency['info']['isLegalMoney']]

fiat_markets = [market for market in exchange.markets.values() if ((market['base'] in fiat_currencies) or (market['quote'] in fiat_currencies))]

for market in fiat_markets:
    print(market['symbol'])
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/binance-fiat.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 15
- Comment lines: 1
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

