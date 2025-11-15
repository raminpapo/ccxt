# Documentation: examples/py/kucoin-fetch-all-deposit-addresses-by-network.py

## File Metadata

- **Path**: `examples/py/kucoin-fetch-all-deposit-addresses-by-network.py`
- **Size**: 554 bytes
- **Lines**: 27
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


exchange = ccxt.kucoin({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_API_SECRET',
    'password': 'YOUR_API_PASSWORD',
    # 'verbose': True,  # for debug output
})

code = 'USDT'

try:
    depositAddresses = exchange.fetch_deposit_addresses_by_network(code)
    pprint(depositAddresses)
except Exception as err:
    print(err)

```

## High-Level Overview

This is a Python file located at `examples/py/kucoin-fetch-all-deposit-addresses-by-network.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 27
- Code lines: 17
- Comment lines: 2
- Blank lines: 8

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
python examples/py/kucoin-fetch-all-deposit-addresses-by-network.py
```

