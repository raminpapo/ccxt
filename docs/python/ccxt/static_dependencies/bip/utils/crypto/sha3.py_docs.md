# Documentation: python/ccxt/static_dependencies/bip/utils/crypto/sha3.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/bip/utils/crypto/sha3.py`
- **Size**: 2,984 bytes
- **Lines**: 100
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# Copyright (c) 2022 Emanuele Bellocchia
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

"""Module for SHA-3 algorithms."""

# Imports
import hashlib
from typing import Union

from Crypto.Hash import SHA3_256, keccak

from ..misc import AlgoUtils


HASHLIB_USE_SHA3_256: bool = "sha3_256" in hashlib.algorithms_available


class Kekkak256:
    """
    Kekkak-256 class.
    It computes digests using Kekkak-256 algorithm.
    """

    @staticmethod
    def QuickDigest(data: Union[bytes, str]) -> bytes:
        """
        Compute the digest (quick version).

        Args:
            data (str or bytes): Data

        Returns:
            bytes: Computed digest
        """
        return keccak.new(data=AlgoUtils.Encode(data), digest_bits=256).digest()

    @staticmethod
    def DigestSize() -> int:
        """
        Get the digest size in bytes.

        Returns:
            int: Digest size in bytes
        """
        return (hashlib.new("sha3_256").digest_size
                if HASHLIB_USE_SHA3_256
                else keccak.new(digest_bits=256).digest_size)


class Sha3_256:     # noqa: N801
    """
    SHA3-256 class.
    It computes digests using SHA3-256 algorithm.
    """

    @staticmethod
    def QuickDigest(data: Union[bytes, str]) -> bytes:
        """
        Compute the digest (quick version).

        Args:
            data (str or bytes): Data

        Returns:
            bytes: Computed digest
        """
        if HASHLIB_USE_SHA3_256:
            return hashlib.new("sha3_256", AlgoUtils.Encode(data)).digest()
        # Use Cryptodome if not implemented in hashlib
        return SHA3_256.new(AlgoUtils.Encode(data)).digest()

    @staticmethod
    def DigestSize() -> int:
        """
        Get the digest size in bytes.

        Returns:
            int: Digest size in bytes
        """
        return (hashlib.new("sha3_256").digest_size
                if HASHLIB_USE_SHA3_256
                else SHA3_256.digest_size)

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/bip/utils/crypto/sha3.py`.

**Classes defined**: Kekkak256, Sha3_256

**Functions defined**: QuickDigest, DigestSize

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 100
- Code lines: 58
- Comment lines: 34
- Blank lines: 8

### Main Components

**Classes** (2):
- `Kekkak256`
- `Sha3_256`

**Functions** (2):
- `DigestSize()`
- `QuickDigest()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/bip/utils/crypto/sha3.py
```

