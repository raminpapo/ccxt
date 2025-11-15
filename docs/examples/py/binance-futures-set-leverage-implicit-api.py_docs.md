# Documentation: examples/py/binance-futures-set-leverage-implicit-api.py

## File Metadata

- **Path**: `examples/py/binance-futures-set-leverage-implicit-api.py`
- **Size**: 555 bytes
- **Lines**: 32
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
    'options': {
        'defaultType': 'future',
    }
})

exchange.load_markets()

symbol = 'ADA/USDT'
market = exchange.market(symbol)
leverage =  10

response = exchange.fapiprivate_post_leverage({
    'symbol': market['id'],
    'leverage': leverage,
})

print(response)

```

## High-Level Overview

This is a Python file located at `examples/py/binance-futures-set-leverage-implicit-api.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 32
- Code lines: 21
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
python examples/py/binance-futures-set-leverage-implicit-api.py
```

