# Documentation: python/ccxt/static_dependencies/ethereum/typing/__init__.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/ethereum/typing/__init__.py`
- **Size**: 913 bytes
- **Lines**: 64
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from importlib.metadata import (
    version as __version,
)

from .abi import (
    Decodable,
    TypeStr,
)
from .bls import (
    BLSPrivateKey,
    BLSPubkey,
    BLSSignature,
)
from .discovery import (
    NodeID,
)
from .encoding import (
    HexStr,
    Primitives,
)
from .enums import (
    ForkName,
)
from .ethpm import (
    URI,
    ContractName,
    Manifest,
)
from .evm import (
    Address,
    AnyAddress,
    BlockIdentifier,
    BlockNumber,
    ChecksumAddress,
    Hash32,
    HexAddress,
)
from .networks import (
    ChainId,
)

__all__ = (
    "Decodable",
    "TypeStr",
    "BLSPrivateKey",
    "BLSPubkey",
    "BLSSignature",
    "NodeID",
    "HexStr",
    "Primitives",
    "ForkName",
    "ChainId",
    "URI",
    "ContractName",
    "Manifest",
    "Address",
    "AnyAddress",
    "BlockIdentifier",
    "BlockNumber",
    "ChecksumAddress",
    "Hash32",
    "HexAddress",
)

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/ethereum/typing/__init__.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 64
- Code lines: 61
- Comment lines: 0
- Blank lines: 3

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/ethereum/typing/__init__.py
```

