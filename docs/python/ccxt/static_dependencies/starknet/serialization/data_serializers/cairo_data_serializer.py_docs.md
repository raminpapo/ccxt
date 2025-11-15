# Documentation: python/ccxt/static_dependencies/starknet/serialization/data_serializers/cairo_data_serializer.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/serialization/data_serializers/cairo_data_serializer.py`
- **Size**: 2,279 bytes
- **Lines**: 72
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from abc import ABC, abstractmethod
from typing import Generator, Generic, List, TypeVar

from .._calldata_reader import CairoData
from .._context import (
    DeserializationContext,
    SerializationContext,
)

# Python type that is accepted by a serializer
# pylint: disable=invalid-name
SerializationType = TypeVar("SerializationType")

# Python type that will be returned from a serializer. Often same as SerializationType.
# pylint: disable=invalid-name
DeserializationType = TypeVar("DeserializationType")


class CairoDataSerializer(ABC, Generic[SerializationType, DeserializationType]):
    """
    Base class for serializing/deserializing data to/from calldata.
    """

    def deserialize(self, data: List[int]) -> DeserializationType:
        """
        Transform calldata into python value.

        :param data: calldata to deserialize.
        :return: defined DeserializationType.
        """
        with DeserializationContext.create(data) as context:
            return self.deserialize_with_context(context)

    def serialize(self, data: SerializationType) -> CairoData:
        """
        Transform python data into calldata.

        :param data: data to serialize.
        :return: calldata.
        """
        with SerializationContext.create() as context:
            serialized_data = list(self.serialize_with_context(context, data))

            return self.remove_units_from_serialized_data(serialized_data)

    @abstractmethod
    def deserialize_with_context(
        self, context: DeserializationContext
    ) -> DeserializationType:
        """
        Transform calldata into python value.

        :param context: context of this deserialization.
        :return: defined DeserializationType.
        """

    @abstractmethod
    def serialize_with_context(
        self, context: SerializationContext, value: SerializationType
    ) -> Generator[int, None, None]:
        """
        Transform python value into calldata.

        :param context: context of this serialization.
        :param value: python value to serialize.
        :return: defined SerializationType.
        """

    @staticmethod
    def remove_units_from_serialized_data(serialized_data: List) -> List:
        return [x for x in serialized_data if x is not None]

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/serialization/data_serializers/cairo_data_serializer.py`.

**Classes defined**: for, CairoDataSerializer

**Functions defined**: remove_units_from_serialized_data, serialize_with_context, serialize, deserialize, deserialize_with_context

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 72
- Code lines: 52
- Comment lines: 14
- Blank lines: 6

### Main Components

**Classes** (1):
- `CairoDataSerializer`

**Functions** (5):
- `deserialize()`
- `deserialize_with_context()`
- `remove_units_from_serialized_data()`
- `serialize()`
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
python python/ccxt/static_dependencies/starknet/serialization/data_serializers/cairo_data_serializer.py
```

