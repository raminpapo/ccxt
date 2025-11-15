# Documentation: python/ccxt/static_dependencies/marshmallow/__init__.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/marshmallow/__init__.py`
- **Size**: 2,365 bytes
- **Lines**: 82
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from __future__ import annotations

import importlib.metadata
import typing

# from packaging.version import Version

from .decorators import (
    post_dump,
    post_load,
    pre_dump,
    pre_load,
    validates,
    validates_schema,
)
from .exceptions import ValidationError
from .schema import Schema, SchemaOpts
from .utils import EXCLUDE, INCLUDE, RAISE, missing, pprint

from . import fields


def __getattr__(name: str) -> typing.Any:
    import warnings

    if name == "__version__":
        warnings.warn(
            "The '__version__' attribute is deprecated and will be removed in"
            " in a future version. Use feature detection or"
            " 'importlib.metadata.version(\"marshmallow\")' instead.",
            DeprecationWarning,
            stacklevel=2,
        )
        return importlib.metadata.version("marshmallow")

    # if name == "__parsed_version__":
    #     warnings.warn(
    #         "The '__parsed_version__' attribute is deprecated and will be removed in"
    #         " in a future version. Use feature detection or"
    #         " 'packaging.Version(importlib.metadata.version(\"marshmallow\"))' instead.",
    #         DeprecationWarning,
    #         stacklevel=2,
    #     )
    #     return Version(importlib.metadata.version("marshmallow"))

    if name == "__version_info__":
        warnings.warn(
            "The '__version_info__' attribute is deprecated and will be removed in"
            " in a future version. Use feature detection or"
            " 'packaging.Version(importlib.metadata.version(\"marshmallow\")).release' instead.",
            DeprecationWarning,
            stacklevel=2,
        )
        # __parsed_version__ = Version(importlib.metadata.version("marshmallow"))
        __version_info__: tuple[int, int, int] | tuple[int, int, int, str, int] = (
            __parsed_version__.release  # type: ignore[assignment]
        )
        if __parsed_version__.pre:
            __version_info__ += __parsed_version__.pre  # type: ignore[assignment]
        return __version_info__

    raise AttributeError(name)


__all__ = [
    "EXCLUDE",
    "INCLUDE",
    "RAISE",
    "Schema",
    "SchemaOpts",
    "fields",
    "validates",
    "validates_schema",
    "pre_dump",
    "post_dump",
    "pre_load",
    "post_load",
    "pprint",
    "ValidationError",
    "missing",
]

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/marshmallow/__init__.py`.

**Functions defined**: __getattr__

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 82
- Code lines: 58
- Comment lines: 11
- Blank lines: 13

### Main Components

**Functions** (1):
- `__getattr__()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/marshmallow/__init__.py
```

