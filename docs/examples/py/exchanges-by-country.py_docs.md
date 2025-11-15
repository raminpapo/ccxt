# Documentation: examples/py/exchanges-by-country.py

## File Metadata

- **Path**: `examples/py/exchanges-by-country.py`
- **Size**: 567 bytes
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


print('CCXT Version:', ccxt.__version__)


country = 'US'
exchanges = []
for exchange_id in ccxt.exchanges:
    try:
        exchange = getattr(ccxt, exchange_id)()
        if country in exchange.countries:
            print(country, exchange_id, exchange.countries)
            exchanges.append(exchange)
    except Exception as e:
        print(type(e).__name__, str(e))

```

## High-Level Overview

This is a Python file located at `examples/py/exchanges-by-country.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 16
- Comment lines: 1
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
python examples/py/exchanges-by-country.py
```

