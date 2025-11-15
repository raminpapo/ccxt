# Documentation: python/ccxt/static_dependencies/starknet/serialization/_calldata_reader.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/serialization/_calldata_reader.py`
- **Size**: 1,135 bytes
- **Lines**: 41
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from typing import List

from ..cairo.felt import CairoData


class OutOfBoundsError(Exception):
    def __init__(self, position: int, requested_size: int, remaining_size: int):
        super().__init__(
            f"Requested {requested_size} elements, {remaining_size} available."
        )
        self.position = position
        self.requested_size = requested_size
        self.remaining_len = remaining_size


class CalldataReader:
    _data: List[int]
    _position: int

    def __init__(self, data: List[int]):
        self._data = data
        self._position = 0

    @property
    def remaining_len(self) -> int:
        return len(self._data) - self._position

    def read(self, size: int) -> CairoData:
        if size < 1:
            raise ValueError("size must be greater than 0")

        if size > self.remaining_len:
            raise OutOfBoundsError(
                position=self._position,
                requested_size=size,
                remaining_size=self.remaining_len,
            )
        data = self._data[self._position : self._position + size]
        self._position += size
        return data

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/serialization/_calldata_reader.py`.

**Classes defined**: OutOfBoundsError, CalldataReader

**Functions defined**: read, __init__, remaining_len

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 31
- Comment lines: 0
- Blank lines: 10

### Main Components

**Classes** (2):
- `CalldataReader`
- `OutOfBoundsError`

**Functions** (3):
- `__init__()`
- `read()`
- `remaining_len()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/serialization/_calldata_reader.py
```

