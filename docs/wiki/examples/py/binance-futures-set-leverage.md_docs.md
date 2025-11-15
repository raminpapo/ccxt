# Documentation: wiki/examples/py/binance-futures-set-leverage.md

## File Metadata

- **Path**: `wiki/examples/py/binance-futures-set-leverage.md`
- **Size**: 328 bytes
- **Lines**: 25
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Binance Futures Set Leverage](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


import ccxt  # noqa: E402


exchange = ccxt.binanceusdm({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
})

exchange.load_markets()

response = exchange.set_leverage(10, 'ADA/USDT')

print(response)
 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/binance-futures-set-leverage.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 13
- Comment lines: 1
- Blank lines: 11

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

