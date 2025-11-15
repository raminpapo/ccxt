# Documentation: wiki/examples/py/binance-futures-positions.md

## File Metadata

- **Path**: `wiki/examples/py/binance-futures-positions.md`
- **Size**: 618 bytes
- **Lines**: 32
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Binance Futures Positions](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint


import ccxt  # noqa: E402

print('CCXT Version:', ccxt.__version__)

exchange = ccxt.binance({
    'apiKey': 'YOUR_TESTNET_API_KEY',
    'secret': 'YOUR_TESTNET_API_SECRET',
    'options': {
        'defaultType': 'future',
    },
})

exchange.set_sandbox_mode(True)  # comment if you're not using the testnet
markets = exchange.load_markets()
exchange.verbose = True  # debug output

balance = exchange.fetch_balance()
positions = balance['info']['positions']
pprint(positions)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/binance-futures-positions.md`.

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

**To execute this Markdown file:**

