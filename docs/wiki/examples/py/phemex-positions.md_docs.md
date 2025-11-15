# Documentation: wiki/examples/py/phemex-positions.md

## File Metadata

- **Path**: `wiki/examples/py/phemex-positions.md`
- **Size**: 1,422 bytes
- **Lines**: 58
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Phemex Positions](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint


import ccxt  # noqa: E402


print('CCXT Version:', ccxt.__version__)

exchange = ccxt.phemex({
    'apiKey': 'YOUR_API_KEY',  # testnet keys if using the testnet sandbox
    'secret': 'YOUR_SECRET',  # testnet keys if using the testnet sandbox
    'options': {
        'defaultType': 'swap',
    },
})

# exchange.set_sandbox_mode(True)  # uncomment to use the testnet sandbox

markets = exchange.load_markets()

# example 1
positions = exchange.fetch_positions(None, {'code':'BTC'})
pprint(positions)

print('------------------------------------------------------------')

# example 2
positions = exchange.fetch_positions(None, {'currency':'BTC'})
pprint(positions)

print('------------------------------------------------------------')

# example 3
balance = exchange.fetch_balance({'code':'BTC'})
pprint(balance['info']['data']['positions'])

print('------------------------------------------------------------')

# example 4
balance = exchange.fetch_balance({'currency':'BTC'})
pprint(balance['info']['data']['positions'])

print('------------------------------------------------------------')

# example 5
# https://github.com/ccxt/ccxt/wiki/Manual#implicit-api-methods
response = exchange.private_get_accounts_accountpositions({'currency': 'BTC'})
pprint(response['data']['positions'])
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/phemex-positions.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 58
- Code lines: 30
- Comment lines: 8
- Blank lines: 20

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

