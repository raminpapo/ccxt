# Documentation: python/ccxt/static_dependencies/starknet/abi/v0/model.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/abi/v0/model.py`
- **Size**: 1,149 bytes
- **Lines**: 45
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from __future__ import annotations

from dataclasses import dataclass
from typing import Dict, Optional, OrderedDict

from ...cairo.data_types import CairoType, StructType


@dataclass
class Abi:
    """
    Dataclass representing class abi. Contains parsed functions, events and structures.
    """

    @dataclass
    class Function:
        """
        Dataclass representing function's abi.
        """

        name: str
        inputs: OrderedDict[str, CairoType]
        outputs: OrderedDict[str, CairoType]

    @dataclass
    class Event:
        """
        Dataclass representing event's abi.
        """

        name: str
        data: OrderedDict[str, CairoType]

    defined_structures: Dict[
        str, StructType
    ]  #: Abi of structures defined by the class.
    functions: Dict[str, Function]  #: Functions defined by the class.
    constructor: Optional[
        Function
    ]  #: Contract's constructor. It is None if class doesn't define one.
    l1_handler: Optional[
        Function
    ]  #: Handler of L1 messages. It is None if class doesn't define one.
    events: Dict[str, Event]  #: Events defined by the class

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/abi/v0/model.py`.

**Classes defined**: Function, Event, doesn, Abi, abi

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 45
- Code lines: 35
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
python python/ccxt/static_dependencies/starknet/abi/v0/model.py
```

