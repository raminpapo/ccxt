# Documentation: python/ccxt/static_dependencies/starknet/common.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/common.py`
- **Size**: 457 bytes
- **Lines**: 16
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from typing import Literal, Union

def int_from_hex(number: Union[str, int]) -> int:
    return number if isinstance(number, int) else int(number, 16)


def int_from_bytes(
    value: bytes,
    byte_order: Literal["big", "little"] = "big",
    signed: bool = False,
) -> int:
    """
    Converts the given bytes object (parsed according to the given byte order) to an integer.
    """
    return int.from_bytes(value, byteorder=byte_order, signed=signed)

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/common.py`.

**Functions defined**: int_from_hex, int_from_bytes

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 16
- Code lines: 12
- Comment lines: 2
- Blank lines: 2

### Main Components

**Functions** (2):
- `int_from_bytes()`
- `int_from_hex()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/common.py
```

