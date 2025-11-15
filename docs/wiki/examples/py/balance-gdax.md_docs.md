# Documentation: wiki/examples/py/balance-gdax.md

## File Metadata

- **Path**: `wiki/examples/py/balance-gdax.md`
- **Size**: 425 bytes
- **Lines**: 25
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [Balance Gdax](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys


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
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/balance-gdax.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 14
- Comment lines: 2
- Blank lines: 9

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `https://api-public.sandbox.gdax.com` (referenced)



## Testing & Execution

**To execute this Markdown file:**

