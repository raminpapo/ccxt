# Documentation: python/ccxt/static_dependencies/marshmallow/exceptions.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/marshmallow/exceptions.py`
- **Size**: 2,326 bytes
- **Lines**: 72
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
"""Exception classes for marshmallow-related errors."""

from __future__ import annotations

import typing

# Key used for schema-level validation errors
SCHEMA = "_schema"


class MarshmallowError(Exception):
    """Base class for all marshmallow-related errors."""


class ValidationError(MarshmallowError):
    """Raised when validation fails on a field or schema.

    Validators and custom fields should raise this exception.

    :param message: An error message, list of error messages, or dict of
        error messages. If a dict, the keys are subitems and the values are error messages.
    :param field_name: Field name to store the error on.
        If `None`, the error is stored as schema-level error.
    :param data: Raw input data.
    :param valid_data: Valid (de)serialized data.
    """

    def __init__(
        self,
        message: str | list | dict,
        field_name: str = SCHEMA,
        data: typing.Mapping[str, typing.Any]
        | typing.Iterable[typing.Mapping[str, typing.Any]]
        | None = None,
        valid_data: list[dict[str, typing.Any]] | dict[str, typing.Any] | None = None,
        **kwargs,
    ):
        self.messages = [message] if isinstance(message, (str, bytes)) else message
        self.field_name = field_name
        self.data = data
        self.valid_data = valid_data
        self.kwargs = kwargs
        super().__init__(message)

    def normalized_messages(self):
        if self.field_name == SCHEMA and isinstance(self.messages, dict):
            return self.messages
        return {self.field_name: self.messages}

    @property
    def messages_dict(self) -> dict[str, typing.Any]:
        if not isinstance(self.messages, dict):
            raise TypeError(
                "cannot access 'messages_dict' when 'messages' is of type "
                + type(self.messages).__name__
            )
        return self.messages


class RegistryError(NameError):
    """Raised when an invalid operation is performed on the serializer
    class registry.
    """


class StringNotCollectionError(MarshmallowError, TypeError):
    """Raised when a string is passed when a list of strings is expected."""


class FieldInstanceResolutionError(MarshmallowError, TypeError):
    """Raised when schema to instantiate is neither a Schema class nor an instance."""

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/marshmallow/exceptions.py`.

**Classes defined**: FieldInstanceResolutionError, for, ValidationError, registry, StringNotCollectionError, nor, MarshmallowError, RegistryError

**Functions defined**: messages_dict, __init__, normalized_messages

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 72
- Code lines: 52
- Comment lines: 10
- Blank lines: 10

### Main Components

**Classes** (5):
- `FieldInstanceResolutionError`
- `MarshmallowError`
- `RegistryError`
- `StringNotCollectionError`
- `ValidationError`

**Functions** (3):
- `__init__()`
- `messages_dict()`
- `normalized_messages()`

**Constants** (1):
- `SCHEMA`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/marshmallow/exceptions.py
```

