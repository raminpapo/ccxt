# Documentation: python/ccxt/static_dependencies/starknet/abi/v2/model.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/abi/v2/model.py`
- **Size**: 2,197 bytes
- **Lines**: 90
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from __future__ import annotations

from dataclasses import dataclass
from typing import Dict, List, Optional, OrderedDict, Union

from ...cairo.data_types import CairoType, EnumType, EventType, StructType


@dataclass
class Abi:
    """
    Dataclass representing class abi. Contains parsed functions, enums, events and structures.
    """

    # pylint: disable=too-many-instance-attributes

    @dataclass
    class Function:
        """
        Dataclass representing function's abi.
        """

        name: str
        inputs: OrderedDict[str, CairoType]
        outputs: List[CairoType]

    @dataclass
    class Constructor:
        """
        Dataclass representing constructor's abi.
        """

        name: str
        inputs: OrderedDict[str, CairoType]

    @dataclass
    class EventStruct:
        """
        Dataclass representing struct event's abi.
        """

        name: str
        members: OrderedDict[str, CairoType]

    @dataclass
    class EventEnum:
        """
        Dataclass representing enum event's abi.
        """

        name: str
        variants: OrderedDict[str, CairoType]

    Event = Union[EventStruct, EventEnum]

    @dataclass
    class Interface:
        """
        Dataclass representing an interface.
        """

        name: str
        items: OrderedDict[
            str, Abi.Function
        ]  # Only functions can be defined in the interface

    @dataclass
    class Impl:
        """
        Dataclass representing an impl.
        """

        name: str
        interface_name: str

    defined_structures: Dict[
        str, StructType
    ]  #: Abi of structures defined by the class.
    defined_enums: Dict[str, EnumType]  #: Abi of enums defined by the class.
    functions: Dict[str, Function]  #: Functions defined by the class.
    events: Dict[str, EventType]  #: Events defined by the class
    constructor: Optional[
        Constructor
    ]  #: Contract's constructor. It is None if class doesn't define one.
    l1_handler: Optional[
        Dict[str, Function]
    ]  #: Handlers of L1 messages. It is None if class doesn't define one.
    interfaces: Dict[str, Interface]
    implementations: Dict[str, Impl]

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/abi/v2/model.py`.

**Classes defined**: EventStruct, Function, doesn, Interface, Abi, EventEnum, Impl, Constructor, constructor, abi

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 90
- Code lines: 69
- Comment lines: 15
- Blank lines: 6

### Main Components

**Classes** (8):
- `Abi`
- `Constructor`
- `EventEnum`
- `EventStruct`
- `Function`
- `Impl`
- `Interface`
- `constructor`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/abi/v2/model.py
```

