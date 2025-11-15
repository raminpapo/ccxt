# Documentation: python/ccxt/static_dependencies/ethereum/abi/base.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/ethereum/abi/base.py`
- **Size**: 4,861 bytes
- **Lines**: 153
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import functools

from ..typing.abi import (
    TypeStr,
)

from .grammar import (
    BasicType,
    TupleType,
    normalize,
    parse,
)


def parse_type_str(expected_base=None, with_arrlist=False):
    """
    Used by BaseCoder subclasses as a convenience for implementing the
    ``from_type_str`` method required by ``ABIRegistry``.  Useful if normalizing
    then parsing a type string with an (optional) expected base is required in
    that method.
    """

    def decorator(old_from_type_str):
        @functools.wraps(old_from_type_str)
        def new_from_type_str(cls, type_str, registry):
            normalized_type_str = normalize(type_str)
            abi_type = parse(normalized_type_str)

            type_str_repr = repr(type_str)
            if type_str != normalized_type_str:
                type_str_repr = "{} (normalized to {})".format(
                    type_str_repr,
                    repr(normalized_type_str),
                )

            if expected_base is not None:
                if not isinstance(abi_type, BasicType):
                    raise ValueError(
                        "Cannot create {} for non-basic type {}".format(
                            cls.__name__,
                            type_str_repr,
                        )
                    )
                if abi_type.base != expected_base:
                    raise ValueError(
                        "Cannot create {} for type {}: expected type with "
                        "base '{}'".format(
                            cls.__name__,
                            type_str_repr,
                            expected_base,
                        )
                    )

            if not with_arrlist and abi_type.arrlist is not None:
                raise ValueError(
                    "Cannot create {} for type {}: expected type with "
                    "no array dimension list".format(
                        cls.__name__,
                        type_str_repr,
                    )
                )
            if with_arrlist and abi_type.arrlist is None:
                raise ValueError(
                    "Cannot create {} for type {}: expected type with "
                    "array dimension list".format(
                        cls.__name__,
                        type_str_repr,
                    )
                )

            # Perform general validation of default solidity types
            abi_type.validate()

            return old_from_type_str(cls, abi_type, registry)

        return classmethod(new_from_type_str)

    return decorator


def parse_tuple_type_str(old_from_type_str):
    """
    Used by BaseCoder subclasses as a convenience for implementing the
    ``from_type_str`` method required by ``ABIRegistry``.  Useful if normalizing
    then parsing a tuple type string is required in that method.
    """

    @functools.wraps(old_from_type_str)
    def new_from_type_str(cls, type_str, registry):
        normalized_type_str = normalize(type_str)
        abi_type = parse(normalized_type_str)

        type_str_repr = repr(type_str)
        if type_str != normalized_type_str:
            type_str_repr = "{} (normalized to {})".format(
                type_str_repr,
                repr(normalized_type_str),
            )

        if not isinstance(abi_type, TupleType):
            raise ValueError(
                "Cannot create {} for non-tuple type {}".format(
                    cls.__name__,
                    type_str_repr,
                )
            )

        abi_type.validate()

        return old_from_type_str(cls, abi_type, registry)

    return classmethod(new_from_type_str)


class BaseCoder:
    """
    Base class for all encoder and decoder classes.
    """

    is_dynamic = False

    def __init__(self, **kwargs):
        cls = type(self)

        # Ensure no unrecognized kwargs were given
        for key, value in kwargs.items():
            if not hasattr(cls, key):
                raise AttributeError(
                    "Property {key} not found on {cls_name} class. "
                    "`{cls_name}.__init__` only accepts keyword arguments which are "
                    "present on the {cls_name} class.".format(
                        key=key,
                        cls_name=cls.__name__,
                    )
                )
            setattr(self, key, value)

        # Validate given combination of kwargs
        self.validate()

    def validate(self):
        pass

    @classmethod
    def from_type_str(
        cls, type_str: TypeStr, registry
    ) -> "BaseCoder":  # pragma: no cover
        """
        Used by :any:`ABIRegistry` to get an appropriate encoder or decoder
        instance for the given type string and type registry.
        """
        raise NotImplementedError("Must implement `from_type_str`")

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/ethereum/abi/base.py`.

**Classes defined**: for, BaseCoder

**Functions defined**: new_from_type_str, parse_type_str, __init__, from_type_str, parse_tuple_type_str, validate, decorator

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 153
- Code lines: 121
- Comment lines: 11
- Blank lines: 21

### Main Components

**Classes** (1):
- `BaseCoder`

**Functions** (7):
- `__init__()`
- `decorator()`
- `from_type_str()`
- `new_from_type_str()`
- `parse_tuple_type_str()`
- `parse_type_str()`
- `validate()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/ethereum/abi/base.py
```

