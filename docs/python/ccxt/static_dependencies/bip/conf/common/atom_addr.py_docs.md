# Documentation: python/ccxt/static_dependencies/bip/conf/common/atom_addr.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/bip/conf/common/atom_addr.py`
- **Size**: 3,442 bytes
- **Lines**: 105
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# Copyright (c) 2021 Emanuele Bellocchia
#
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
# THE SOFTWARE.

"""Module for Atom address encoding/decoding."""

# Imports
from typing import Any, Union

from bip_utils.addr.addr_dec_utils import AddrDecUtils
from bip_utils.addr.addr_key_validator import AddrKeyValidator
from bip_utils.addr.iaddr_decoder import IAddrDecoder
from bip_utils.addr.iaddr_encoder import IAddrEncoder
from bip_utils.bech32 import Bech32ChecksumError, Bech32Decoder, Bech32Encoder
from bip_utils.ecc import IPublicKey
from bip_utils.utils.crypto import Hash160


class AtomAddrDecoder(IAddrDecoder):
    """
    Atom address decoder class.
    It allows the Atom address decoding.
    """

    @staticmethod
    def DecodeAddr(addr: str,
                   **kwargs: Any) -> bytes:
        """
        Decode an Algorand address to bytes.

        Args:
            addr (str): Address string

        Other Parameters:
            hrp (str): Expected HRP

        Returns:
            bytes: Public key hash bytes

        Raises:
            ValueError: If the address encoding is not valid
        """
        hrp = kwargs["hrp"]

        try:
            addr_dec_bytes = Bech32Decoder.Decode(hrp, addr)
        except Bech32ChecksumError as ex:
            raise ValueError("Invalid bech32 checksum") from ex

        AddrDecUtils.ValidateLength(addr_dec_bytes,
                                    Hash160.DigestSize())
        return addr_dec_bytes


class AtomAddrEncoder(IAddrEncoder):
    """
    Atom address encoder class.
    It allows the Atom address encoding.
    """

    @staticmethod
    def EncodeKey(pub_key: Union[bytes, IPublicKey],
                  **kwargs: Any) -> str:
        """
        Encode a public key to Atom address.

        Args:
            pub_key (bytes or IPublicKey): Public key bytes or object

        Other Parameters:
            hrp (str): HRP

        Returns:
            str: Address string

        Raises:
            ValueError: If the public key is not valid
            TypeError: If the public key is not secp256k1
        """
        hrp = kwargs["hrp"]

        pub_key_obj = AddrKeyValidator.ValidateAndGetSecp256k1Key(pub_key)
        return Bech32Encoder.Encode(hrp,
                                    Hash160.QuickDigest(pub_key_obj.RawCompressed().ToBytes()))


# Deprecated: only for compatibility, Encoder class shall be used instead
AtomAddr = AtomAddrEncoder

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/bip/conf/common/atom_addr.py`.

**Classes defined**: shall, AtomAddrEncoder, AtomAddrDecoder

**Functions defined**: DecodeAddr, EncodeKey

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 105
- Code lines: 61
- Comment lines: 32
- Blank lines: 12

### Main Components

**Classes** (2):
- `AtomAddrDecoder`
- `AtomAddrEncoder`

**Functions** (2):
- `DecodeAddr()`
- `EncodeKey()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/bip/conf/common/atom_addr.py
```

