# Documentation: python/ccxt/static_dependencies/starknet/utils/iterable.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/utils/iterable.py`
- **Size**: 302 bytes
- **Lines**: 14
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from typing import Iterable, TypeVar, Union

T = TypeVar("T")


# pyright: reportGeneralTypeIssues=false
def ensure_iterable(value: Union[T, Iterable[T]]) -> Iterable[T]:
    try:
        iter(value)
        # Now we now it is iterable
        return value
    except TypeError:
        return [value]

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/utils/iterable.py`.

**Functions defined**: ensure_iterable

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 14
- Code lines: 8
- Comment lines: 2
- Blank lines: 4

### Main Components

**Functions** (1):
- `ensure_iterable()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/utils/iterable.py
```

