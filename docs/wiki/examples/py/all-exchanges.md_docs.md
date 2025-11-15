# Documentation: wiki/examples/py/all-exchanges.md

## File Metadata

- **Path**: `wiki/examples/py/all-exchanges.md`
- **Size**: 437 bytes
- **Lines**: 25
- **Type**: Markdown
- **Extension**: .md


## Original Source Code

```markdown
- [All Exchanges](./examples/py/)


 ```python
 # -*- coding: utf-8 -*-

import os
import sys
from pprint import pprint


import ccxt  # noqa: E402


print('CCXT Version:', ccxt.__version__)

for exchange_id in ccxt.exchanges:
    try:
        exchange = getattr(ccxt, exchange_id)()
        print(exchange_id)
        # do what you want with this exchange
        # pprint(dir(exchange))
    except Exception as e:
        print(e) 
```
```

## High-Level Overview

This is a Markdown file located at `wiki/examples/py/all-exchanges.md`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 25
- Code lines: 14
- Comment lines: 3
- Blank lines: 8

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Markdown file:**

