# Documentation: python/ccxt/static_dependencies/bip/utils/crypto/blake2.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/bip/utils/crypto/blake2.py`
- **Size**: 4,984 bytes
- **Lines**: 192
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

"""Module for BLAKE-2 algorithms."""

# Imports
import hashlib
from abc import ABC, abstractmethod
from typing import Union

from ..misc import AlgoUtils


class Blake2b:
    """
    BLAKE2b class.
    It computes digests using BLAKE2b algorithm.
    """

    @staticmethod
    def QuickDigest(data: Union[bytes, str],
                    digest_size: int,
                    key: Union[bytes, str] = b"",
                    salt: Union[bytes, str] = b"") -> bytes:
        """
        Compute the digest (quick version).

        Args:
            data (str or bytes)           : Data
            digest_size (int)             : Digest size
            key ((str or bytes, optional) : Key (default: empty)
            salt ((str or bytes, optional): Salt (default: empty)

        Returns:
            bytes: Computed digest
        """
        return hashlib.blake2b(AlgoUtils.Encode(data),
                               digest_size=digest_size,
                               key=AlgoUtils.Encode(key),
                               salt=AlgoUtils.Encode(salt)).digest()


class _Blake2bWithSpecificSize(ABC):
    """Abstract class for Blake2b with specific digest size."""

    @classmethod
    def QuickDigest(cls,
                    data: Union[bytes, str],
                    key: Union[bytes, str] = b"",
                    salt: Union[bytes, str] = b"") -> bytes:
        """
        Compute the digest (quick version).

        Args:
            data (str or bytes)          : Data
            key (str or bytes, optional) : Key bytes (default: empty)
            salt (str or bytes, optional): Salt bytes (default: empty)

        Returns:
            bytes: Computed digest
        """
        return Blake2b.QuickDigest(data, cls.DigestSize(), key, salt)

    @staticmethod
    @abstractmethod
    def DigestSize() -> int:
        """
        Get the digest size in bytes.

        Returns:
            int: Digest size in bytes
        """


class Blake2b32(_Blake2bWithSpecificSize):
    """
    BLAKE2b-32 class.
    It computes digests using BLAKE2b-32 algorithm.
    """

    @staticmethod
    def DigestSize() -> int:
        """
        Get the digest size in bytes.

        Returns:
            int: Digest size in bytes
        """
        return 4


class Blake2b40(_Blake2bWithSpecificSize):
    """
    BLAKE2b-40 class.
    It computes digests using BLAKE2b-40 algorithm.
    """

    @staticmethod
    def DigestSize() -> int:
        """
        Get the digest size in bytes.

        Returns:
            int: Digest size in bytes
        """
        return 5


class Blake2b160(_Blake2bWithSpecificSize):
    """
    BLAKE2b-160 class.
    It computes digests using BLAKE2b-160 algorithm.
    """

    @staticmethod
    def DigestSize() -> int:
        """
        Get the digest size in bytes.

        Returns:
            int: Digest size in bytes
        """
        return 20


class Blake2b224(_Blake2bWithSpecificSize):
    """
    BLAKE2b-224 class.
    It computes digests using BLAKE2b-224 algorithm.
    """

    @staticmethod
    def DigestSize() -> int:
        """
        Get the digest size in bytes.

        Returns:
            int: Digest size in bytes
        """
        return 28


class Blake2b256(_Blake2bWithSpecificSize):
    """
    BLAKE2b-256 class.
    It computes digests using BLAKE2b-256 algorithm.
    """

    @staticmethod
    def DigestSize() -> int:
        """
        Get the digest size in bytes.

        Returns:
            int: Digest size in bytes
        """
        return 32


class Blake2b512(_Blake2bWithSpecificSize):
    """
    BLAKE2b-512 class.
    It computes digests using BLAKE2b-512 algorithm.
    """

    @staticmethod
    def DigestSize() -> int:
        """
        Get the digest size in bytes.

        Returns:
            int: Digest size in bytes
        """
        return 64

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/bip/utils/crypto/blake2.py`.

**Classes defined**: _Blake2bWithSpecificSize, Blake2b256, for, Blake2b224, Blake2b32, Blake2b160, Blake2b40, Blake2b, Blake2b512

**Functions defined**: QuickDigest, DigestSize

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 192
- Code lines: 132
- Comment lines: 54
- Blank lines: 6

### Main Components

**Classes** (8):
- `Blake2b`
- `Blake2b160`
- `Blake2b224`
- `Blake2b256`
- `Blake2b32`
- `Blake2b40`
- `Blake2b512`
- `_Blake2bWithSpecificSize`

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
python python/ccxt/static_dependencies/bip/utils/crypto/blake2.py
```

