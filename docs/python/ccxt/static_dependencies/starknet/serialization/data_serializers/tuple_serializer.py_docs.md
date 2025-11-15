# Documentation: python/ccxt/static_dependencies/starknet/serialization/data_serializers/tuple_serializer.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/serialization/data_serializers/tuple_serializer.py`
- **Size**: 964 bytes
- **Lines**: 37
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from dataclasses import dataclass
from typing import Generator, Iterable, List, Tuple

from .._context import (
    DeserializationContext,
    SerializationContext,
)
from ._common import (
    deserialize_to_list,
    serialize_from_list,
)
from .cairo_data_serializer import (
    CairoDataSerializer,
)


@dataclass
class TupleSerializer(CairoDataSerializer[Iterable, Tuple]):
    """
    Serializer for tuples without named fields.
    Can serialize any iterable.
    Deserializes data to a python tuple.

    Example:
    (1,2,(3,4)) => [1,2,3,4]
    """

    serializers: List[CairoDataSerializer]

    def deserialize_with_context(self, context: DeserializationContext) -> Tuple:
        return tuple(deserialize_to_list(self.serializers, context))

    def serialize_with_context(
        self, context: SerializationContext, value: Iterable
    ) -> Generator[int, None, None]:
        yield from serialize_from_list(self.serializers, context, [*value])

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/serialization/data_serializers/tuple_serializer.py`.

**Classes defined**: TupleSerializer

**Functions defined**: serialize_with_context, deserialize_with_context

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 29
- Comment lines: 2
- Blank lines: 6

### Main Components

**Classes** (1):
- `TupleSerializer`

**Functions** (2):
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
python python/ccxt/static_dependencies/starknet/serialization/data_serializers/tuple_serializer.py
```

