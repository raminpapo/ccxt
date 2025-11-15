# Documentation: python/ccxt/static_dependencies/marshmallow_dataclass/collection_field.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/marshmallow_dataclass/collection_field.py`
- **Size**: 1,640 bytes
- **Lines**: 52
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import typing

import marshmallow


class Sequence(marshmallow.fields.List):
    """
    A sequence field, basically an immutable version of the list field.
    """

    def _deserialize(  # type: ignore[override]
        self,
        value: typing.Any,
        attr: typing.Any,
        data: typing.Any,
        **kwargs: typing.Any,
    ) -> typing.Optional[typing.Sequence[typing.Any]]:
        optional_list = super()._deserialize(value, attr, data, **kwargs)
        return None if optional_list is None else tuple(optional_list)


class Set(marshmallow.fields.List):
    """
    A set field. A set is an unordered/mutable collection of unique elements, same for frozenset
    except it's immutable.

    Notes:
        Beware the a Set guarantees uniqueness in the resulting list but in return the item's order
        will be random. So if the order matters, use a List or Sequence !
    """

    def __init__(
        self,
        cls_or_instance: typing.Union[marshmallow.fields.Field, type],
        frozen: bool = False,
        **kwargs,
    ):
        super().__init__(cls_or_instance, **kwargs)
        self.set_type: typing.Type[typing.Union[frozenset, set]] = (
            frozenset if frozen else set
        )

    def _deserialize(  # type: ignore[override]
        self,
        value: typing.Any,
        attr: typing.Any,
        data: typing.Any,
        **kwargs: typing.Any,
    ) -> typing.Union[typing.Set[typing.Any], typing.FrozenSet[typing.Any], None]:
        optional_list = super()._deserialize(value, attr, data, **kwargs)
        return None if optional_list is None else self.set_type(optional_list)

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/marshmallow_dataclass/collection_field.py`.

**Classes defined**: Sequence, Set

**Functions defined**: __init__, _deserialize

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 52
- Code lines: 42
- Comment lines: 7
- Blank lines: 3

### Main Components

**Classes** (2):
- `Sequence`
- `Set`

**Functions** (2):
- `__init__()`
- `_deserialize()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/marshmallow_dataclass/collection_field.py
```

