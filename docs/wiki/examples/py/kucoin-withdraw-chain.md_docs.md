# Documentation: wiki/examples/py/kucoin-withdraw-chain.md

## File Metadata

- **Path**: `wiki/examples/py/kucoin-withdraw-chain.md`
- **Size**: 780 bytes
- **Lines**: 40
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Kucoin Withdraw Chain](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/kucoin-withdraw-chain.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 40
- Code lines: 26
- Comment lines: 2
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

