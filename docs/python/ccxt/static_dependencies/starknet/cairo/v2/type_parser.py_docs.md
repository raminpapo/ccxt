# Documentation: python/ccxt/static_dependencies/starknet/cairo/v2/type_parser.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/cairo/v2/type_parser.py`
- **Size**: 2,506 bytes
- **Lines**: 78
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from __future__ import annotations

from typing import Dict, Union

from ...abi.v2.parser_transformer import parse
from ..data_types import (
    CairoType,
    EnumType,
    EventType,
    StructType,
    TypeIdentifier,
)


class UnknownCairoTypeError(ValueError):
    """
    Error thrown when TypeParser finds type that was not declared prior to parsing.
    """

    type_name: str

    def __init__(self, type_name: str):
        super().__init__(
            # pylint: disable=line-too-long
            f"Type '{type_name}' is not defined. Please report this issue at https://github.com/software-mansion/starknet.py/issues"
        )
        self.type_name = type_name


class TypeParser:
    """
    Low level utility class for parsing Cairo types that can be used in external methods.
    """

    defined_types: Dict[str, Union[StructType, EnumType, EventType]]

    def __init__(
        self, defined_types: Dict[str, Union[StructType, EnumType, EventType]]
    ):
        """
        TypeParser constructor.

        :param defined_types: dictionary containing all defined types. For now, they can only be structures.
        """
        self.defined_types = defined_types
        for name, defined_type in defined_types.items():
            if name != defined_type.name:
                raise ValueError(
                    f"Keys must match name of type, '{name}' != '{defined_type.name}'."
                )

    def update_defined_types(
        self, defined_types: Dict[str, Union[StructType, EnumType, EventType]]
    ) -> None:
        self.defined_types.update(defined_types)

    def add_defined_type(
        self, defined_type: Union[StructType, EnumType, EventType]
    ) -> None:
        self.defined_types.update({defined_type.name: defined_type})

    def parse_inline_type(self, type_string: str) -> CairoType:
        """
        Inline type is one that can be used inline, for instance as return type. For instance
        (core::felt252, (), (core::felt252,)). Structure can only be referenced in inline type, can't be defined
        this way.

        :param type_string: type to parse.
        """
        parsed = parse(type_string, self.defined_types)
        if isinstance(parsed, TypeIdentifier):
            for defined_name in self.defined_types.keys():
                if parsed.name == defined_name.split("<")[0].strip(":"):
                    return self.defined_types[defined_name]
            raise UnknownCairoTypeError(parsed.name)

        return parsed

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/cairo/v2/type_parser.py`.

**Classes defined**: UnknownCairoTypeError, for, TypeParser

**Functions defined**: update_defined_types, __init__, parse_inline_type, add_defined_type

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 78
- Code lines: 60
- Comment lines: 9
- Blank lines: 9

### Main Components

**Classes** (2):
- `TypeParser`
- `UnknownCairoTypeError`

**Functions** (4):
- `__init__()`
- `add_defined_type()`
- `parse_inline_type()`
- `update_defined_types()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/cairo/v2/type_parser.py
```

