# Documentation: python/ccxt/static_dependencies/ethereum/hexbytes/main.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/ethereum/hexbytes/main.py`
- **Size**: 1,768 bytes
- **Lines**: 66
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import sys
from typing import (
    TYPE_CHECKING,
    Type,
    Union,
    cast,
    overload,
)

from ._utils import (
    to_bytes,
)

if TYPE_CHECKING:
    from typing import (
        SupportsIndex,
    )

BytesLike = Union[bool, bytearray, bytes, int, str, memoryview]


class HexBytes(bytes):
    """
    HexBytes is a *very* thin wrapper around the python built-in :class:`bytes` class.

    It has these three changes:
        1. Accepts more initializing values, like hex strings, non-negative integers,
           and booleans
        2. Returns hex with prefix '0x' from :meth:`HexBytes.hex`
        3. The representation at console is in hex
    """

    def __new__(cls: Type[bytes], val: BytesLike) -> "HexBytes":
        bytesval = to_bytes(val)
        return cast(HexBytes, super().__new__(cls, bytesval))  # type: ignore  # https://github.com/python/typeshed/issues/2630  # noqa: E501

    def hex(
        self, sep: Union[str, bytes] = None, bytes_per_sep: "SupportsIndex" = 1
    ) -> str:
        """
        Output hex-encoded bytes, with an "0x" prefix.

        Everything following the "0x" is output exactly like :meth:`bytes.hex`.
        """
        return "0x" + super().hex()

    @overload
    def __getitem__(self, key: "SupportsIndex") -> int:  # noqa: F811
        ...

    @overload  # noqa: F811
    def __getitem__(self, key: slice) -> "HexBytes":  # noqa: F811
        ...

    def __getitem__(  # noqa: F811
        self, key: Union["SupportsIndex", slice]
    ) -> Union[int, bytes, "HexBytes"]:
        result = super().__getitem__(key)
        if hasattr(result, "hex"):
            return type(self)(result)
        else:
            return result

    def __repr__(self) -> str:
        return f"HexBytes({self.hex()!r})"

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/ethereum/hexbytes/main.py`.

**Classes defined**: HexBytes

**Functions defined**: __getitem__, hex, __repr__, __new__

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 66
- Code lines: 52
- Comment lines: 4
- Blank lines: 10

### Main Components

**Classes** (1):
- `HexBytes`

**Functions** (4):
- `__getitem__()`
- `__new__()`
- `__repr__()`
- `hex()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/ethereum/hexbytes/main.py
```

