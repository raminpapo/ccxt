# Documentation: examples/py/balance-gdax.py

## File Metadata

- **Path**: `examples/py/balance-gdax.py`
- **Size**: 491 bytes
- **Lines**: 22
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

gdax = ccxt.gdax({
    'apiKey': "YOUR_API_KEY",
    'secret': "YOUR_SECRET",
    'password': "YOUR_PASSWORD",
    'verbose': True,  # switch it to False if you don't want the HTTP log
})

# move gdax to sandbox
gdax.urls['api'] = 'https://api-public.sandbox.gdax.com'

print(gdax.fetch_balance())

```

## High-Level Overview

This is a Python file located at `examples/py/balance-gdax.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 13
- Comment lines: 2
- Blank lines: 7

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `https://api-public.sandbox.gdax.com` (referenced)



## Testing & Execution

**To execute this Python file:**

```bash
python examples/py/balance-gdax.py
```

