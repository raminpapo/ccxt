# Documentation: python/ccxt/static_dependencies/starknet/hash/address.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/hash/address.py`
- **Size**: 2,259 bytes
- **Lines**: 80
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from typing import Sequence

from ..constants import CONTRACT_ADDRESS_PREFIX, L2_ADDRESS_UPPER_BOUND
from .utils import (
    HEX_PREFIX,
    _starknet_keccak,
    compute_hash_on_elements,
    encode_uint,
    get_bytes_length,
)


def compute_address(
    *,
    class_hash: int,
    constructor_calldata: Sequence[int],
    salt: int,
    deployer_address: int = 0,
) -> int:
    """
    Computes the contract address in the Starknet network - a unique identifier of the contract.

    :param class_hash: class hash of the contract
    :param constructor_calldata: calldata for the contract constructor
    :param salt: salt used to calculate contract address
    :param deployer_address: address of the deployer (if not provided default 0 is used)
    :return: Contract's address
    """

    constructor_calldata_hash = compute_hash_on_elements(data=constructor_calldata)
    raw_address = compute_hash_on_elements(
        data=[
            CONTRACT_ADDRESS_PREFIX,
            deployer_address,
            salt,
            class_hash,
            constructor_calldata_hash,
        ],
    )

    return raw_address % L2_ADDRESS_UPPER_BOUND


def get_checksum_address(address: str) -> str:
    """
    Outputs formatted checksum address.

    Follows implementation of starknet.js. It is not compatible with EIP55 as it treats hex string as encoded number,
    instead of encoding it as ASCII string.

    :param address: Address to encode
    :return: Checksum address
    """
    if not address.lower().startswith(HEX_PREFIX):
        raise ValueError(f"{address} is not a valid hexadecimal address.")

    int_address = int(address, 16)
    string_address = address[2:].zfill(64)

    address_in_bytes = encode_uint(int_address, get_bytes_length(int_address))
    address_hash = _starknet_keccak(address_in_bytes)

    result = "".join(
        (
            char.upper()
            if char.isalpha() and (address_hash >> 256 - 4 * i - 1) & 1
            else char
        )
        for i, char in enumerate(string_address)
    )

    return f"{HEX_PREFIX}{result}"


def is_checksum_address(address: str) -> bool:
    """
    Checks if provided string is in a checksum address format.
    """
    return get_checksum_address(address) == address

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/hash/address.py`.

**Classes defined**: hash

**Functions defined**: get_checksum_address, is_checksum_address, compute_address

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 80
- Code lines: 63
- Comment lines: 7
- Blank lines: 10

### Main Components

**Functions** (3):
- `compute_address()`
- `get_checksum_address()`
- `is_checksum_address()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/hash/address.py
```

