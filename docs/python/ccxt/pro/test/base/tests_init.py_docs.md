# Documentation: python/ccxt/pro/test/base/tests_init.py

## File Metadata

- **Path**: `python/ccxt/pro/test/base/tests_init.py`
- **Size**: 771 bytes
- **Lines**: 21
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import os
import sys

root = os.path.dirname(os.path.dirname(os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))))
sys.path.append(root)

from asyncio import run

from ccxt.pro.test.base.test_order_book import test_ws_order_book  # noqa: F401
from ccxt.pro.test.base.test_cache import test_ws_cache  # noqa: F401
# todo : from ccxt.pro.test.base.test_close import test_ws_close  # noqa: F401
from ccxt.pro.test.base.test_future import test_ws_future  # noqa: F401
from ccxt.pro.test.base.test_abnormal_close import test_abnormal_close  # noqa: F401

def test_base_init_ws():
    test_ws_order_book()
    test_ws_cache()
    # todo : run(test_ws_close())
    run(test_ws_future())
    # run(test_abnormal_close()) stays in infinite loop in travis

```

## High-Level Overview

This is a Python file located at `python/ccxt/pro/test/base/tests_init.py`.

**Functions defined**: test_base_init_ws

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 21
- Code lines: 13
- Comment lines: 3
- Blank lines: 5

### Main Components

**Functions** (1):
- `test_base_init_ws()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Implements caching mechanisms



## Related Files

No explicit file references found.



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
pytest python/ccxt/pro/test/base/tests_init.py
```

