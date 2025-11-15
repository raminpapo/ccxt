# Documentation: python/ccxt/static_dependencies/marshmallow_dataclass/lazy_class_attribute.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/marshmallow_dataclass/lazy_class_attribute.py`
- **Size**: 1,070 bytes
- **Lines**: 46
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from typing import Any, Callable, Optional


__all__ = ("lazy_class_attribute",)


class LazyClassAttribute:
    """Descriptor decorator implementing a class-level, read-only
    property, which caches its results on the class(es) on which it
    operates.
    """

    __slots__ = ("func", "name", "called", "forward_value")

    def __init__(
        self,
        func: Callable[..., Any],
        name: Optional[str] = None,
        forward_value: Any = None,
    ):
        self.func = func
        self.name = name
        self.called = False
        self.forward_value = forward_value

    def __get__(self, instance, cls=None):
        if not cls:
            cls = type(instance)

        # avoid recursion
        if self.called:
            return self.forward_value

        self.called = True

        setattr(cls, self.name, self.func())

        # "getattr" is used to handle bounded methods
        return getattr(cls, self.name)

    def __set_name__(self, owner, name):
        self.name = self.name or name


lazy_class_attribute = LazyClassAttribute

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/marshmallow_dataclass/lazy_class_attribute.py`.

**Classes defined**: LazyClassAttribute

**Functions defined**: __get__, __init__, __set_name__

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 46
- Code lines: 29
- Comment lines: 4
- Blank lines: 13

### Main Components

**Classes** (1):
- `LazyClassAttribute`

**Functions** (3):
- `__get__()`
- `__init__()`
- `__set_name__()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Implements caching mechanisms



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/marshmallow_dataclass/lazy_class_attribute.py
```

