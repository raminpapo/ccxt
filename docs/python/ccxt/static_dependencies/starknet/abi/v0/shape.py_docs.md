# Documentation: python/ccxt/static_dependencies/starknet/abi/v0/shape.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/abi/v0/shape.py`
- **Size**: 1,349 bytes
- **Lines**: 64
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# TODO (#1260): update pylint to 3.1.0 and remove pylint disable
# pylint: disable=too-many-ancestors
import sys
from typing import List, Literal, Union

if sys.version_info < (3, 11):
    from typing_extensions import NotRequired, TypedDict
else:
    from typing import NotRequired, TypedDict

STRUCT_ENTRY = "struct"
FUNCTION_ENTRY = "function"
CONSTRUCTOR_ENTRY = "constructor"
L1_HANDLER_ENTRY = "l1_handler"
EVENT_ENTRY = "event"


class TypedMemberDict(TypedDict):
    name: str
    type: str


class StructMemberDict(TypedMemberDict):
    offset: NotRequired[int]


class StructDict(TypedDict):
    type: Literal["struct"]
    name: str
    size: int
    members: List[StructMemberDict]


class FunctionBaseDict(TypedDict):
    name: str
    inputs: List[TypedMemberDict]
    outputs: List[TypedMemberDict]
    stateMutability: NotRequired[Literal["view"]]


class FunctionDict(FunctionBaseDict):
    type: Literal["function"]


class ConstructorDict(FunctionBaseDict):
    type: Literal["constructor"]


class L1HandlerDict(FunctionBaseDict):
    type: Literal["l1_handler"]


class EventDict(TypedDict):
    name: str
    type: Literal["event"]
    data: List[TypedMemberDict]
    keys: List[TypedMemberDict]


AbiDictEntry = Union[
    StructDict, FunctionDict, ConstructorDict, L1HandlerDict, EventDict
]
AbiDictList = List[AbiDictEntry]

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/abi/v0/shape.py`.

**Classes defined**: FunctionBaseDict, EventDict, StructDict, StructMemberDict, FunctionDict, TypedMemberDict, L1HandlerDict, ConstructorDict

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 64
- Code lines: 41
- Comment lines: 2
- Blank lines: 21

### Main Components

**Classes** (8):
- `ConstructorDict`
- `EventDict`
- `FunctionBaseDict`
- `FunctionDict`
- `L1HandlerDict`
- `StructDict`
- `StructMemberDict`
- `TypedMemberDict`

**Constants** (5):
- `CONSTRUCTOR_ENTRY`
- `EVENT_ENTRY`
- `FUNCTION_ENTRY`
- `L1_HANDLER_ENTRY`
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
python python/ccxt/static_dependencies/starknet/abi/v0/shape.py
```

