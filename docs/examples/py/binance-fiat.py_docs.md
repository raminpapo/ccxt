# Documentation: examples/py/binance-fiat.py

## File Metadata

- **Path**: `examples/py/binance-fiat.py`
- **Size**: 639 bytes
- **Lines**: 25
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

## High-Level Overview

This is a Python file located at `examples/py/binance-fiat.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 14
- Comment lines: 1
- Blank lines: 10

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
python examples/py/binance-fiat.py
```

