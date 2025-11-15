# Documentation: wiki/examples/py/sign-in.md

## File Metadata

- **Path**: `wiki/examples/py/sign-in.md`
- **Size**: 834 bytes
- **Lines**: 37
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Sign In](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/sign-in.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 26
- Comment lines: 2
- Blank lines: 9

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

