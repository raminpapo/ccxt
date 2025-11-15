# Documentation: examples/py/source-ip-address.py

## File Metadata

- **Path**: `examples/py/source-ip-address.py`
- **Size**: 975 bytes
- **Lines**: 38
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

import os
import sys
import requests
from pprint import pprint

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
sys.path.append(root + '/python')

import ccxt  # noqa: E402


# configure the source IP address
ip_address = '192.168.1.2'  # YOUR EXTERNAL IP ADDRESS HERE
session = requests.Session()
for prefix in ('http://', 'https://'):
    session.get_adapter(prefix).init_poolmanager(
        # those are default values from HTTPAdapter's constructor
        connections=requests.adapters.DEFAULT_POOLSIZE,
        maxsize=requests.adapters.DEFAULT_POOLSIZE,
        # This should be a tuple of (address, port). Port 0 means auto-selection.
        source_address=(ip_address, 0),
    )


exchange = ccxt.ftx({
    'session': session,
    # ... other config properties here if necessary ...
})


markets = exchange.load_markets()
exchange.verbose = True

ticker = exchange.fetch_ticker('BTC/USD')
pprint(ticker)

```

## High-Level Overview

This is a Python file located at `examples/py/source-ip-address.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 38
- Code lines: 22
- Comment lines: 5
- Blank lines: 11

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
python examples/py/source-ip-address.py
```

