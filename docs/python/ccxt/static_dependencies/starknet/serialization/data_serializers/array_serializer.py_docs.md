# Documentation: python/ccxt/static_dependencies/starknet/serialization/data_serializers/array_serializer.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/serialization/data_serializers/array_serializer.py`
- **Size**: 1,219 bytes
- **Lines**: 44
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from dataclasses import dataclass
from typing import Generator, Iterable, List

from .._context import (
    DeserializationContext,
    SerializationContext,
)
from ..data_serializers._common import (
    deserialize_to_list,
    serialize_from_list,
)
from ..data_serializers.cairo_data_serializer import (
    CairoDataSerializer,
)


@dataclass
class ArraySerializer(CairoDataSerializer[Iterable, List]):
    """
    Serializer for arrays. In abi they are represented as a pointer to a type.
    Can serialize any iterable and prepends its length to resulting list.
    Deserializes data to a list.

    Examples:
    [1,2,3] => [3,1,2,3]
    [] => [0]
    """

    inner_serializer: CairoDataSerializer

    def deserialize_with_context(self, context: DeserializationContext) -> List:
        with context.push_entity("len"):
            [size] = context.reader.read(1)

        return deserialize_to_list([self.inner_serializer] * size, context)

    def serialize_with_context(
        self, context: SerializationContext, value: List
    ) -> Generator[int, None, None]:
        yield len(value)
        yield from serialize_from_list(
            [self.inner_serializer] * len(value), context, value
        )

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/serialization/data_serializers/array_serializer.py`.

**Classes defined**: ArraySerializer

**Functions defined**: serialize_with_context, deserialize_with_context

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 44
- Code lines: 35
- Comment lines: 2
- Blank lines: 7

### Main Components

**Classes** (1):
- `ArraySerializer`

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
python python/ccxt/static_dependencies/starknet/serialization/data_serializers/array_serializer.py
```

