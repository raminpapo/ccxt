# Documentation: examples/py/sign-in.py

## File Metadata

- **Path**: `examples/py/sign-in.py`
- **Size**: 905 bytes
- **Lines**: 34
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


exchange = ccxt.bitmart({
    'apiKey': 'YOUR_API_KEY',
    'secret': 'YOUR_SECRET',
    'uid': 'YOUR_UID',
})

while True:
    try:
        print('---------------------------------------------------------------')
        datetime = exchange.iso8601 (exchange.milliseconds ())
        print(datetime)
        balance = exchange.fetch_balance()  # this will trigger a sign_in when needed
        pprint(balance)
        # handle the response how you want or do other calls...
    except ccxt.AuthenticationError as e:
        error_message = str(e)
        if 'accessToken' in error_message:
            exchange.sign_in()
        else:
            print(str(e))
            sys.exit()

```

## High-Level Overview

This is a Python file located at `examples/py/sign-in.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 25
- Comment lines: 2
- Blank lines: 7

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
python examples/py/sign-in.py
```

