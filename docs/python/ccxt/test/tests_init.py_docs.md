# Documentation: python/ccxt/test/tests_init.py

## File Metadata

- **Path**: `python/ccxt/test/tests_init.py`
- **Size**: 1,212 bytes
- **Lines**: 41
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

from tests_helpers import get_cli_arg_value, IS_SYNCHRONOUS, argvExchange, argvSymbol, argvMethod

try:
    import asyncio
except ImportError:
    asyncio = None

from base.tests_init import base_tests_init  # noqa: F401
from ccxt.pro.test.base.tests_init import test_base_init_ws  # noqa: F401

# fix : https://github.com/aio-libs/aiodns/issues/86
import sys
if sys.platform == 'win32':
    asyncio.set_event_loop_policy(asyncio.WindowsSelectorEventLoopPolicy())

# ########### args ###########
isWs = get_cli_arg_value('--ws')
isBaseTests = get_cli_arg_value('--baseTests')
runAll = get_cli_arg_value('--all')

# ###### base tests #######
if (isBaseTests):
    if (isWs):
        test_base_init_ws()
        print('base WS tests passed!')
    else:
        base_tests_init()
        print('base REST tests passed!')
    if not runAll:
        exit(0)

# ###### exchange tests #######
if (IS_SYNCHRONOUS):
    from tests_sync import testMainClass as testMainClassSync
    testMainClassSync().init(argvExchange, argvSymbol, argvMethod)
else:
    from tests_async import testMainClass as testMainClassAsync
    asyncio.run(testMainClassAsync().init(argvExchange, argvSymbol, argvMethod))

```

## High-Level Overview

This is a Python file located at `python/ccxt/test/tests_init.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 28
- Comment lines: 5
- Blank lines: 8

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Uses async/await for non-blocking operations



## Related Files

No explicit file references found.



## Testing & Execution

This appears to be a test file.

**To run this test:**
```bash
pytest python/ccxt/test/tests_init.py
```

