# Documentation: python/ccxt/static_dependencies/ethereum/utils/types.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/ethereum/utils/types.py`
- **Size**: 1,074 bytes
- **Lines**: 55
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import collections.abc
import numbers
from typing import (
    Any,
)

bytes_types = (bytes, bytearray)
integer_types = (int,)
text_types = (str,)
string_types = (bytes, str, bytearray)


def is_integer(value: Any) -> bool:
    return isinstance(value, integer_types) and not isinstance(value, bool)


def is_bytes(value: Any) -> bool:
    return isinstance(value, bytes_types)


def is_text(value: Any) -> bool:
    return isinstance(value, text_types)


def is_string(value: Any) -> bool:
    return isinstance(value, string_types)


def is_boolean(value: Any) -> bool:
    return isinstance(value, bool)


def is_dict(obj: Any) -> bool:
    return isinstance(obj, collections.abc.Mapping)


def is_list_like(obj: Any) -> bool:
    return not is_string(obj) and isinstance(obj, collections.abc.Sequence)


def is_list(obj: Any) -> bool:
    return isinstance(obj, list)


def is_tuple(obj: Any) -> bool:
    return isinstance(obj, tuple)


def is_null(obj: Any) -> bool:
    return obj is None


def is_number(obj: Any) -> bool:
    return isinstance(obj, numbers.Number)

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/ethereum/utils/types.py`.

**Functions defined**: is_null, is_integer, is_bytes, is_list_like, is_dict, is_tuple, is_text, is_boolean, is_list, is_string

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 55
- Code lines: 31
- Comment lines: 0
- Blank lines: 24

### Main Components

**Functions** (11):
- `is_boolean()`
- `is_bytes()`
- `is_dict()`
- `is_integer()`
- `is_list()`
- `is_list_like()`
- `is_null()`
- `is_number()`
- `is_string()`
- `is_text()`
- `is_tuple()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/ethereum/utils/types.py
```

