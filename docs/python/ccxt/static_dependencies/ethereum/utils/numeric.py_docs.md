# Documentation: python/ccxt/static_dependencies/ethereum/utils/numeric.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/ethereum/utils/numeric.py`
- **Size**: 1,190 bytes
- **Lines**: 44
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from abc import (
    ABC,
    abstractmethod,
)
import decimal
import numbers
from typing import (
    Any,
    TypeVar,
    Union,
)


class Comparable(ABC):
    @abstractmethod
    def __lt__(self, other: Any) -> bool:
        ...

    @abstractmethod
    def __gt__(self, other: Any) -> bool:
        ...


TComparable = Union[Comparable, numbers.Real, int, float, decimal.Decimal]


TValue = TypeVar("TValue", bound=TComparable)


def clamp(lower_bound: TValue, upper_bound: TValue, value: TValue) -> TValue:
    # The `mypy` ignore statements here are due to doing a comparison of
    # `Union` types which isn't allowed. (per cburgdorf). This approach was
    # chosen over using `typing.overload` to define multiple signatures for
    # each comparison type here since the added value of "proper" typing
    # doesn't seem to justify the complexity of having a bunch of different
    # signatures defined. The external library perspective on this function
    # should still be adequate under this approach
    if value < lower_bound:  # type: ignore
        return lower_bound
    elif value > upper_bound:  # type: ignore
        return upper_bound
    else:
        return value

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/ethereum/utils/numeric.py`.

**Classes defined**: Comparable

**Functions defined**: __lt__, __gt__, clamp

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 27
- Comment lines: 7
- Blank lines: 10

### Main Components

**Classes** (1):
- `Comparable`

**Functions** (3):
- `__gt__()`
- `__lt__()`
- `clamp()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/ethereum/utils/numeric.py
```

