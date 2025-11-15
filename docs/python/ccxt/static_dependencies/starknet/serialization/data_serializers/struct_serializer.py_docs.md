# Documentation: python/ccxt/static_dependencies/starknet/serialization/data_serializers/struct_serializer.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/serialization/data_serializers/struct_serializer.py`
- **Size**: 941 bytes
- **Lines**: 37
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from dataclasses import dataclass
from typing import Dict, Generator, OrderedDict

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


@dataclass
class StructSerializer(CairoDataSerializer[Dict, Dict]):
    """
    Serializer of custom structures.
    Can serialize a dictionary.
    Deserializes data to a dictionary.

    Example:
    {"a": 1, "b": 2} => [1,2]
    """

    serializers: OrderedDict[str, CairoDataSerializer]

    def deserialize_with_context(self, context: DeserializationContext) -> Dict:
        return deserialize_to_dict(self.serializers, context)

    def serialize_with_context(
        self, context: SerializationContext, value: Dict
    ) -> Generator[int, None, None]:
        yield from serialize_from_dict(self.serializers, context, value)

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/serialization/data_serializers/struct_serializer.py`.

**Classes defined**: StructSerializer

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
- `StructSerializer`

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
python python/ccxt/static_dependencies/starknet/serialization/data_serializers/struct_serializer.py
```

