# Documentation: python/ccxt/static_dependencies/ethereum/hexbytes/_utils.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/ethereum/hexbytes/_utils.py`
- **Size**: 1,687 bytes
- **Lines**: 55
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import binascii
from typing import (
    Union,
)


def to_bytes(val: Union[bool, bytearray, bytes, int, str, memoryview]) -> bytes:
    """
    Equivalent to: `eth_utils.hexstr_if_str(eth_utils.to_bytes, val)` .

    Convert a hex string, integer, or bool, to a bytes representation.
    Alternatively, pass through bytes or bytearray as a bytes value.
    """
    if isinstance(val, bytes):
        return val
    elif isinstance(val, str):
        return hexstr_to_bytes(val)
    elif isinstance(val, bytearray):
        return bytes(val)
    elif isinstance(val, bool):
        return b"\x01" if val else b"\x00"
    elif isinstance(val, int):
        # Note that this int check must come after the bool check, because
        #   isinstance(True, int) is True
        if val < 0:
            raise ValueError(f"Cannot convert negative integer {val} to bytes")
        else:
            return to_bytes(hex(val))
    elif isinstance(val, memoryview):
        return bytes(val)
    else:
        raise TypeError(f"Cannot convert {val!r} of type {type(val)} to bytes")


def hexstr_to_bytes(hexstr: str) -> bytes:
    if hexstr.startswith(("0x", "0X")):
        non_prefixed_hex = hexstr[2:]
    else:
        non_prefixed_hex = hexstr

    # if the hex string is odd-length, then left-pad it to an even length
    if len(hexstr) % 2:
        padded_hex = "0" + non_prefixed_hex
    else:
        padded_hex = non_prefixed_hex

    try:
        ascii_hex = padded_hex.encode("ascii")
    except UnicodeDecodeError:
        raise ValueError(
            f"hex string {padded_hex} may only contain [0-9a-fA-F] characters"
        )
    else:
        return binascii.unhexlify(ascii_hex)

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/ethereum/hexbytes/_utils.py`.

**Functions defined**: hexstr_to_bytes, to_bytes

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 55
- Code lines: 44
- Comment lines: 5
- Blank lines: 6

### Main Components

**Functions** (2):
- `hexstr_to_bytes()`
- `to_bytes()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/ethereum/hexbytes/_utils.py
```

