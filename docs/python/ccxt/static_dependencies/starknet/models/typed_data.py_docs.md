# Documentation: python/ccxt/static_dependencies/starknet/models/typed_data.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/models/typed_data.py`
- **Size**: 815 bytes
- **Lines**: 46
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
"""
TypedDict structures for TypedData
"""

from enum import Enum
from typing import Any, Dict, List, Optional, TypedDict

class Revision(Enum):
    """
    Enum representing the revision of the specification to be used.
    """

    V0 = 0
    V1 = 1


class ParameterDict(TypedDict):
    """
    TypedDict representing a Parameter object
    """

    name: str
    type: str


class StarkNetDomainDict(TypedDict):
    """
    TypedDict representing a domain object (both StarkNetDomain, StarknetDomain).
    """

    name: str
    version: str
    chainId: str
    revision: Optional[Revision]


class TypedDataDict(TypedDict):
    """
    TypedDict representing a TypedData object
    """

    types: Dict[str, List[ParameterDict]]
    primaryType: str
    domain: StarkNetDomainDict
    message: Dict[str, Any]

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/models/typed_data.py`.

**Classes defined**: TypedDataDict, StarkNetDomainDict, Revision, ParameterDict

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 46
- Code lines: 33
- Comment lines: 10
- Blank lines: 3

### Main Components

**Classes** (4):
- `ParameterDict`
- `Revision`
- `StarkNetDomainDict`
- `TypedDataDict`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/models/typed_data.py
```

