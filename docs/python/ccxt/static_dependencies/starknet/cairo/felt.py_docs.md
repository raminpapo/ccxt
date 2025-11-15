# Documentation: python/ccxt/static_dependencies/starknet/cairo/felt.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/cairo/felt.py`
- **Size**: 1,708 bytes
- **Lines**: 65
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from typing import List

from ..constants import FIELD_PRIME

CairoData = List[int]


MAX_UINT256 = (1 << 256) - 1
MIN_UINT256 = 0


def uint256_range_check(value: int):
    if not MIN_UINT256 <= value <= MAX_UINT256:
        raise ValueError(
            f"Uint256 is expected to be in range [0;2**256), got: {value}."
        )


MIN_FELT = -FIELD_PRIME // 2
MAX_FELT = FIELD_PRIME // 2


def is_in_felt_range(value: int) -> bool:
    return 0 <= value < FIELD_PRIME


def cairo_vm_range_check(value: int):
    if not is_in_felt_range(value):
        raise ValueError(
            f"Felt is expected to be in range [0; {FIELD_PRIME}), got: {value}."
        )


def encode_shortstring(text: str) -> int:
    """
    A function which encodes short string value (at most 31 characters) into cairo felt (MSB as first character)

    :param text: A short string value in python
    :return: Short string value encoded into felt
    """
    if len(text) > 31:
        raise ValueError(
            f"Shortstring cannot be longer than 31 characters, got: {len(text)}."
        )

    try:
        text_bytes = text.encode("ascii")
    except UnicodeEncodeError as u_err:
        raise ValueError(f"Expected an ascii string. Found: {repr(text)}.") from u_err
    value = int.from_bytes(text_bytes, "big")

    cairo_vm_range_check(value)
    return value


def decode_shortstring(value: int) -> str:
    """
    A function which decodes a felt value to short string (at most 31 characters)

    :param value: A felt value
    :return: Decoded string which is corresponds to that felt
    """
    cairo_vm_range_check(value)
    return "".join([chr(i) for i in value.to_bytes(31, byteorder="big")]).lstrip("\x00")

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/cairo/felt.py`.

**Functions defined**: decode_shortstring, uint256_range_check, which, is_in_felt_range, cairo_vm_range_check, encode_shortstring

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 65
- Code lines: 44
- Comment lines: 4
- Blank lines: 17

### Main Components

**Functions** (6):
- `cairo_vm_range_check()`
- `decode_shortstring()`
- `encode_shortstring()`
- `is_in_felt_range()`
- `uint256_range_check()`
- `which()`

**Constants** (4):
- `MAX_FELT`
- `MAX_UINT256`
- `MIN_FELT`
- `MIN_UINT256`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/cairo/felt.py
```

