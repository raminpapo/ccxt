# Documentation: examples/py/balance-kraken.py

## File Metadata

- **Path**: `examples/py/balance-kraken.py`
- **Size**: 383 bytes
- **Lines**: 18
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

kraken = ccxt.kraken({
    'apiKey': "YOUR_API_KEY",
    'secret': "YOUR_SECRET",
    'verbose': True,  # switch it to False if you don't want the HTTP log
})

print(kraken.fetch_balance())

```

## High-Level Overview

This is a Python file located at `examples/py/balance-kraken.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 18
- Code lines: 11
- Comment lines: 1
- Blank lines: 6

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
python examples/py/balance-kraken.py
```

