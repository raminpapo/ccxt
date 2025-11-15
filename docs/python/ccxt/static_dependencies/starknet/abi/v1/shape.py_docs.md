# Documentation: python/ccxt/static_dependencies/starknet/abi/v1/shape.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/abi/v1/shape.py`
- **Size**: 927 bytes
- **Lines**: 48
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from typing import List, Literal, Optional, TypedDict, Union

ENUM_ENTRY = "enum"
STRUCT_ENTRY = "struct"
FUNCTION_ENTRY = "function"
EVENT_ENTRY = "event"


class TypeDict(TypedDict):
    type: str


class TypedParameterDict(TypeDict):
    name: str


class StructDict(TypedDict):
    type: Literal["struct"]
    name: str
    members: List[TypedParameterDict]


class FunctionBaseDict(TypedDict):
    name: str
    inputs: List[TypedParameterDict]
    outputs: List[TypeDict]
    state_mutability: Optional[Literal["external", "view"]]


class FunctionDict(FunctionBaseDict):
    type: Literal["function"]


class EventDict(TypedDict):
    name: str
    type: Literal["event"]
    inputs: List[TypedParameterDict]


class EnumDict(TypedDict):
    type: Literal["enum"]
    name: str
    variants: List[TypedParameterDict]


AbiDictEntry = Union[StructDict, FunctionDict, EventDict, EnumDict]
AbiDictList = List[AbiDictEntry]

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/abi/v1/shape.py`.

**Classes defined**: FunctionBaseDict, EventDict, TypedParameterDict, EnumDict, TypeDict, StructDict, FunctionDict

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 48
- Code lines: 30
- Comment lines: 0
- Blank lines: 18

### Main Components

**Classes** (7):
- `EnumDict`
- `EventDict`
- `FunctionBaseDict`
- `FunctionDict`
- `StructDict`
- `TypeDict`
- `TypedParameterDict`

**Constants** (4):
- `ENUM_ENTRY`
- `EVENT_ENTRY`
- `FUNCTION_ENTRY`
- `STRUCT_ENTRY`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/abi/v1/shape.py
```

