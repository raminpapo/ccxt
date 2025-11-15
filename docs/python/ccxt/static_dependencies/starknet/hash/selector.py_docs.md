# Documentation: python/ccxt/static_dependencies/starknet/hash/selector.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/hash/selector.py`
- **Size**: 474 bytes
- **Lines**: 17
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ..constants import (
    DEFAULT_ENTRY_POINT_NAME,
    DEFAULT_ENTRY_POINT_SELECTOR,
    DEFAULT_L1_ENTRY_POINT_NAME,
)
from ..hash.utils import _starknet_keccak


def get_selector_from_name(func_name: str) -> int:
    """
    Returns the selector of a contract's function name.
    """
    if func_name in [DEFAULT_ENTRY_POINT_NAME, DEFAULT_L1_ENTRY_POINT_NAME]:
        return DEFAULT_ENTRY_POINT_SELECTOR

    return _starknet_keccak(data=func_name.encode("ascii"))

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/hash/selector.py`.

**Functions defined**: get_selector_from_name, name

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 17
- Code lines: 13
- Comment lines: 2
- Blank lines: 2

### Main Components

**Functions** (2):
- `get_selector_from_name()`
- `name()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/hash/selector.py
```

