# Documentation: python/ccxt/async_support/base/ws/__init__.py

## File Metadata

- **Path**: `python/ccxt/async_support/base/ws/__init__.py`
- **Size**: 1,791 bytes
- **Lines**: 39
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

from ccxt.base import errors

# -----------------------------------------------------------------------------

from ccxt.base import decimal_to_precision

from ccxt import BaseError                  # noqa: F401
from ccxt import ExchangeError              # noqa: F401
from ccxt import NotSupported               # noqa: F401
from ccxt import AuthenticationError        # noqa: F401
from ccxt import PermissionDenied           # noqa: F401
from ccxt import AccountSuspended           # noqa: F401
from ccxt import InvalidNonce               # noqa: F401
from ccxt import InsufficientFunds          # noqa: F401
from ccxt import InvalidOrder               # noqa: F401
from ccxt import OrderNotFound              # noqa: F401
from ccxt import OrderNotCached             # noqa: F401
from ccxt import DuplicateOrderId           # noqa: F401
from ccxt import CancelPending              # noqa: F401
from ccxt import NetworkError               # noqa: F401
from ccxt import DDoSProtection             # noqa: F401
from ccxt import RateLimitExceeded          # noqa: F401
from ccxt import RequestTimeout             # noqa: F401
from ccxt import ExchangeNotAvailable       # noqa: F401
from ccxt import OnMaintenance              # noqa: F401
from ccxt import InvalidAddress             # noqa: F401
from ccxt import AddressPending             # noqa: F401
from ccxt import ArgumentsRequired          # noqa: F401
from ccxt import BadRequest                 # noqa: F401
from ccxt import BadResponse                # noqa: F401
from ccxt import NullResponse               # noqa: F401
from ccxt import OrderImmediatelyFillable   # noqa: F401
from ccxt import OrderNotFillable           # noqa: F401


__all__ = decimal_to_precision.__all__ + errors.__all__  # noqa: F405

```

## High-Level Overview

This is a Python file located at `python/ccxt/async_support/base/ws/__init__.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 30
- Comment lines: 2
- Blank lines: 7

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Implements caching mechanisms



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/async_support/base/ws/__init__.py
```

