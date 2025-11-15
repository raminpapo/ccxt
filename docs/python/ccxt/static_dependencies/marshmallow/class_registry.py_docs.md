# Documentation: python/ccxt/static_dependencies/marshmallow/class_registry.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/marshmallow/class_registry.py`
- **Size**: 2,790 bytes
- **Lines**: 95
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
"""A registry of :class:`Schema <marshmallow.Schema>` classes. This allows for string
lookup of schemas, which may be used with
class:`fields.Nested <marshmallow.fields.Nested>`.

.. warning::

    This module is treated as private API.
    Users should not need to use this module directly.
"""

from __future__ import annotations

import typing

from .exceptions import RegistryError

if typing.TYPE_CHECKING:
    from . import Schema

    SchemaType = typing.Type[Schema]

# {
#   <class_name>: <list of class objects>
#   <module_path_to_class>: <list of class objects>
# }
_registry = {}  # type: dict[str, list[SchemaType]]


def register(classname: str, cls: SchemaType) -> None:
    """Add a class to the registry of serializer classes. When a class is
    registered, an entry for both its classname and its full, module-qualified
    path are added to the registry.

    Example: ::

        class MyClass:
            pass


        register("MyClass", MyClass)
        # Registry:
        # {
        #   'MyClass': [path.to.MyClass],
        #   'path.to.MyClass': [path.to.MyClass],
        # }

    """
    # Module where the class is located
    module = cls.__module__
    # Full module path to the class
    # e.g. user.schemas.UserSchema
    fullpath = ".".join([module, classname])
    # If the class is already registered; need to check if the entries are
    # in the same module as cls to avoid having multiple instances of the same
    # class in the registry
    if classname in _registry and not any(
        each.__module__ == module for each in _registry[classname]
    ):
        _registry[classname].append(cls)
    elif classname not in _registry:
        _registry[classname] = [cls]

    # Also register the full path
    if fullpath not in _registry:
        _registry.setdefault(fullpath, []).append(cls)
    else:
        # If fullpath does exist, replace existing entry
        _registry[fullpath] = [cls]
    return None


def get_class(classname: str, all: bool = False) -> list[SchemaType] | SchemaType:
    """Retrieve a class from the registry.

    :raises: marshmallow.exceptions.RegistryError if the class cannot be found
        or if there are multiple entries for the given class name.
    """
    try:
        classes = _registry[classname]
    except KeyError as error:
        raise RegistryError(
            f"Class with name {classname!r} was not found. You may need "
            "to import the class."
        ) from error
    if len(classes) > 1:
        if all:
            return _registry[classname]
        raise RegistryError(
            f"Multiple classes with name {classname!r} "
            "were found. Please use the full, "
            "module-qualified path."
        )
    else:
        return _registry[classname][0]

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/marshmallow/class_registry.py`.

**Classes defined**: objects, to, in, is, MyClass, cannot, from

**Functions defined**: register, get_class

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 95
- Code lines: 58
- Comment lines: 23
- Blank lines: 14

### Main Components

**Classes** (2):
- `MyClass`
- `is`

**Functions** (2):
- `get_class()`
- `register()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/marshmallow/class_registry.py
```

