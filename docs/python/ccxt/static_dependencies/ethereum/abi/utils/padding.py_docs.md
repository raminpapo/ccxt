# Documentation: python/ccxt/static_dependencies/ethereum/abi/utils/padding.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/ethereum/abi/utils/padding.py`
- **Size**: 426 bytes
- **Lines**: 28
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from ...utils.toolz import (
    curry,
)


@curry
def zpad(value: bytes, length: int) -> bytes:
    return value.rjust(length, b"\x00")


zpad32 = zpad(length=32)


@curry
def zpad_right(value: bytes, length: int) -> bytes:
    return value.ljust(length, b"\x00")


zpad32_right = zpad_right(length=32)


@curry
def fpad(value: bytes, length: int) -> bytes:
    return value.rjust(length, b"\xff")


fpad32 = fpad(length=32)

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/ethereum/abi/utils/padding.py`.

**Functions defined**: fpad, zpad, zpad_right

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 15
- Comment lines: 0
- Blank lines: 13

### Main Components

**Functions** (3):
- `fpad()`
- `zpad()`
- `zpad_right()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/ethereum/abi/utils/padding.py
```

