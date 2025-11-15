# Documentation: python/ccxt/static_dependencies/starknet/constants.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/constants.py`
- **Size**: 1,281 bytes
- **Lines**: 40
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from pathlib import Path

# Address came from starkware-libs/starknet-addresses repository: https://github.com/starkware-libs/starknet-addresses
FEE_CONTRACT_ADDRESS = (
    "0x049d36570d4e46f48e99674bd3fcc84644ddd6b96f7c741b1562b82f9e004dc7"
)

DEFAULT_DEPLOYER_ADDRESS = (
    "0x041a78e741e5aF2fEc34B695679bC6891742439f7AFB8484Ecd7766661aD02BF"
)

API_VERSION = 0

RPC_CONTRACT_NOT_FOUND_ERROR = 20
RPC_INVALID_MESSAGE_SELECTOR_ERROR = 21
RPC_CLASS_HASH_NOT_FOUND_ERROR = 28
RPC_CONTRACT_ERROR = 40

DEFAULT_ENTRY_POINT_NAME = "__default__"
DEFAULT_L1_ENTRY_POINT_NAME = "__l1_default__"
DEFAULT_ENTRY_POINT_SELECTOR = 0
DEFAULT_DECLARE_SENDER_ADDRESS = 1

# MAX_STORAGE_ITEM_SIZE and ADDR_BOUND must be consistent with the corresponding constant in
# starkware/starknet/common/storage.cairo.
MAX_STORAGE_ITEM_SIZE = 256
ADDR_BOUND = 2**251 - MAX_STORAGE_ITEM_SIZE

FIELD_PRIME = 0x800000000000011000000000000000000000000000000000000000000000001
EC_ORDER = 0x800000000000010FFFFFFFFFFFFFFFFB781126DCAE7B2321E66A241ADC64D2F

# From cairo-lang
# int_from_bytes(b"STARKNET_CONTRACT_ADDRESS")
CONTRACT_ADDRESS_PREFIX = 523065374597054866729014270389667305596563390979550329787219
L2_ADDRESS_UPPER_BOUND = 2**251 - 256

QUERY_VERSION_BASE = 2**128

ROOT_PATH = Path(__file__).parent

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/constants.py`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 40
- Code lines: 24
- Comment lines: 5
- Blank lines: 11

### Main Components

**Constants** (19):
- `ADDR_BOUND`
- `API_VERSION`
- `CONTRACT_ADDRESS_PREFIX`
- `DEFAULT_DECLARE_SENDER_ADDRESS`
- `DEFAULT_DEPLOYER_ADDRESS`
- `DEFAULT_ENTRY_POINT_NAME`
- `DEFAULT_ENTRY_POINT_SELECTOR`
- `DEFAULT_L1_ENTRY_POINT_NAME`
- `EC_ORDER`
- `FEE_CONTRACT_ADDRESS`
- `FIELD_PRIME`
- `L2_ADDRESS_UPPER_BOUND`
- `MAX_STORAGE_ITEM_SIZE`
- `QUERY_VERSION_BASE`
- `ROOT_PATH`
- `RPC_CLASS_HASH_NOT_FOUND_ERROR`
- `RPC_CONTRACT_ERROR`
- `RPC_CONTRACT_NOT_FOUND_ERROR`
- `RPC_INVALID_MESSAGE_SELECTOR_ERROR`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/constants.py
```

