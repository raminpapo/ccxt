# Documentation: python/ccxt/static_dependencies/starknet/serialization/data_serializers/named_tuple_serializer.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/serialization/data_serializers/named_tuple_serializer.py`
- **Size**: 1,809 bytes
- **Lines**: 59
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from dataclasses import dataclass
from typing import Dict, Generator, NamedTuple, OrderedDict, Union

from .._context import (
    DeserializationContext,
    SerializationContext,
)
from ._common import (
    deserialize_to_dict,
    serialize_from_dict,
)
from .cairo_data_serializer import (
    CairoDataSerializer,
)
from ..tuple_dataclass import TupleDataclass


@dataclass
class NamedTupleSerializer(
    CairoDataSerializer[Union[Dict, NamedTuple, TupleDataclass], TupleDataclass]
):
    """
    Serializer for tuples with named fields.
    Can serialize a dictionary, a named tuple and TupleDataclass.
    Deserializes data to a TupleDataclass.

    Example:
    {"a": 1, "b": 2} => [1,2]
    """

    serializers: OrderedDict[str, CairoDataSerializer]

    def deserialize_with_context(
        self, context: DeserializationContext
    ) -> TupleDataclass:
        as_dictionary = deserialize_to_dict(self.serializers, context)
        return TupleDataclass.from_dict(as_dictionary)

    def serialize_with_context(
        self,
        context: SerializationContext,
        value: Union[Dict, NamedTuple, TupleDataclass],
    ) -> Generator[int, None, None]:
        # We can't use isinstance(value, NamedTuple), because there is no NamedTuple type.
        context.ensure_valid_type(
            value,
            isinstance(value, (dict, TupleDataclass)) or self._is_namedtuple(value),
            "dict, NamedTuple or TupleDataclass",
        )

        # noinspection PyUnresolvedReferences, PyProtectedMember
        values: Dict = value if isinstance(value, dict) else value._asdict()

        yield from serialize_from_dict(self.serializers, context, values)

    @staticmethod
    def _is_namedtuple(value) -> bool:
        return isinstance(value, tuple) and hasattr(value, "_fields")

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/serialization/data_serializers/named_tuple_serializer.py`.

**Classes defined**: NamedTupleSerializer

**Functions defined**: serialize_with_context, _is_namedtuple, deserialize_with_context

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 59
- Code lines: 46
- Comment lines: 4
- Blank lines: 9

### Main Components

**Classes** (1):
- `NamedTupleSerializer`

**Functions** (3):
- `_is_namedtuple()`
- `deserialize_with_context()`
- `serialize_with_context()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/serialization/data_serializers/named_tuple_serializer.py
```

