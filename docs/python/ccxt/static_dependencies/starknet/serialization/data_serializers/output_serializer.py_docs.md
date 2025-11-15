# Documentation: python/ccxt/static_dependencies/starknet/serialization/data_serializers/output_serializer.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/serialization/data_serializers/output_serializer.py`
- **Size**: 1,151 bytes
- **Lines**: 41
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from dataclasses import dataclass, field
from typing import Dict, Generator, List, Tuple

from .._context import (
    DeserializationContext,
    SerializationContext,
)
from .cairo_data_serializer import (
    CairoDataSerializer,
)


@dataclass
class OutputSerializer(CairoDataSerializer[List, Tuple]):
    """
    Serializer for function output.
    Can't serialize anything.
    Deserializes data to a Tuple.

    Example:
        [1, 1, 1] => (340282366920938463463374607431768211457)
    """

    serializers: List[CairoDataSerializer] = field(init=True)

    def deserialize_with_context(self, context: DeserializationContext) -> Tuple:
        result = []

        for index, serializer in enumerate(self.serializers):
            with context.push_entity("output[" + str(index) + "]"):
                result.append(serializer.deserialize_with_context(context))

        return tuple(result)

    def serialize_with_context(
        self, context: SerializationContext, value: Dict
    ) -> Generator[int, None, None]:
        raise ValueError(
            "Output serializer can't be used to transform python data into calldata."
        )

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/serialization/data_serializers/output_serializer.py`.

**Classes defined**: OutputSerializer

**Functions defined**: serialize_with_context, deserialize_with_context, output

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 41
- Code lines: 31
- Comment lines: 2
- Blank lines: 8

### Main Components

**Classes** (1):
- `OutputSerializer`

**Functions** (3):
- `deserialize_with_context()`
- `output()`
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
python python/ccxt/static_dependencies/starknet/serialization/data_serializers/output_serializer.py
```

