# Documentation: python/ccxt/static_dependencies/starknet/abi/v1/model.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/abi/v1/model.py`
- **Size**: 995 bytes
- **Lines**: 40
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from __future__ import annotations

from dataclasses import dataclass
from typing import Dict, List, OrderedDict

from ...cairo.data_types import CairoType, EnumType, StructType


@dataclass
class Abi:
    """
    Dataclass representing class abi. Contains parsed functions, enums, events and structures.
    """

    @dataclass
    class Function:
        """
        Dataclass representing function's abi.
        """

        name: str
        inputs: OrderedDict[str, CairoType]
        outputs: List[CairoType]

    @dataclass
    class Event:
        """
        Dataclass representing event's abi.
        """

        name: str
        inputs: OrderedDict[str, CairoType]

    defined_structures: Dict[
        str, StructType
    ]  #: Abi of structures defined by the class.
    defined_enums: Dict[str, EnumType]  #: Abi of enums defined by the class.
    functions: Dict[str, Function]  #: Functions defined by the class.
    events: Dict[str, Event]  #: Events defined by the class

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/abi/v1/model.py`.

**Classes defined**: Abi, Function, Event, abi

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 40
- Code lines: 30
- Comment lines: 6
- Blank lines: 4

### Main Components

**Classes** (3):
- `Abi`
- `Event`
- `Function`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/abi/v1/model.py
```

