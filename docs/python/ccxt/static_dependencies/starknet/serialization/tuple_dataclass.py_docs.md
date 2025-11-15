# Documentation: python/ccxt/static_dependencies/starknet/serialization/tuple_dataclass.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/serialization/tuple_dataclass.py`
- **Size**: 2,108 bytes
- **Lines**: 60
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from __future__ import annotations

from dataclasses import dataclass, fields, make_dataclass
from typing import Dict, Optional, Tuple


@dataclass(frozen=True, eq=False)
class TupleDataclass:
    """
    Dataclass that behaves like a tuple at the same time. Used when data has defined order and names.
    For instance in case of named tuples or function responses.
    """

    # getattr is called when attribute is not found in object. For instance when using object.unknown_attribute.
    # This way pyright will know that there might be some arguments it doesn't know about and will stop complaining
    # about some fields that don't exist statically.
    def __getattr__(self, item):
        # This should always fail - only attributes that don't exist end up in here.
        # We use __getattribute__ to get the native error.
        return super().__getattribute__(item)

    def __getitem__(self, item: int):
        field = fields(self)[item]
        return getattr(self, field.name)

    def __iter__(self):
        return (getattr(self, field.name) for field in fields(self))

    def as_tuple(self) -> Tuple:
        """
        Creates a regular tuple from TupleDataclass.
        """
        return tuple(self)

    def as_dict(self) -> Dict:
        """
        Creates a regular dict from TupleDataclass.
        """
        return {field.name: getattr(self, field.name) for field in fields(self)}

    # Added for backward compatibility with previous implementation based on NamedTuple
    def _asdict(self):
        return self.as_dict()

    def __eq__(self, other):
        if isinstance(other, TupleDataclass):
            return self.as_tuple() == other.as_tuple()
        return self.as_tuple() == other

    @staticmethod
    def from_dict(data: Dict, *, name: Optional[str] = None) -> TupleDataclass:
        result_class = make_dataclass(
            name or "TupleDataclass",
            fields=[(key, type(value)) for key, value in data.items()],
            bases=(TupleDataclass,),
            frozen=True,
            eq=False,
        )
        return result_class(**data)

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/serialization/tuple_dataclass.py`.

**Classes defined**: TupleDataclass

**Functions defined**: _asdict, as_tuple, from_dict, responses, __getitem__, __iter__, as_dict, __getattr__, __eq__

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 60
- Code lines: 42
- Comment lines: 12
- Blank lines: 6

### Main Components

**Classes** (1):
- `TupleDataclass`

**Functions** (9):
- `__eq__()`
- `__getattr__()`
- `__getitem__()`
- `__iter__()`
- `_asdict()`
- `as_dict()`
- `as_tuple()`
- `from_dict()`
- `responses()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/serialization/tuple_dataclass.py
```

