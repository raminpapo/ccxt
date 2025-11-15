# Documentation: examples/py/kucoin-withdraw-chain.py

## File Metadata

- **Path**: `examples/py/kucoin-withdraw-chain.py`
- **Size**: 837 bytes
- **Lines**: 37
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt  # noqa: E402


print('CCXT Version:', ccxt.__version__)

exchange = ccxt.kucoin({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
    'password': 'YOUR_API_PASSWORD',
})

markets = exchange.load_markets()

# exchange.verbose = True  # uncomment for debugging purposes

try:
    code = 'USDT'
    amount = 123
    address = '0x3010c3486f1c16cb608ba3e53e3597c9a3b01f41'
    tag = None
    params = {
        'chain': 'TRC20',  # 'ERC20', 'TRC20', default is ERC20
    }
    response = exchange.withdraw(code, amount, address, tag, params)
    pprint(response)
except Exception as e:
    print(type(e).__name__, str(e))

```

## High-Level Overview

This is a Python file located at `examples/py/kucoin-withdraw-chain.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 25
- Comment lines: 2
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
python examples/py/kucoin-withdraw-chain.py
```

