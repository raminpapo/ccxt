# Documentation: python/ccxt/static_dependencies/bip/utils/crypto/hash160.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/bip/utils/crypto/hash160.py`
- **Size**: 1,843 bytes
- **Lines**: 58
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

"""Module for HASH160 algorithm."""

# Imports
from typing import Union

from .ripemd import Ripemd160
from .sha2 import Sha256


class Hash160:
    """
    HASH160 class.
    It computes digests using HASH160 algorithm.
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
        return Ripemd160.QuickDigest(Sha256.QuickDigest(data))

    @staticmethod
    def DigestSize() -> int:
        """
        Get the digest size in bytes.

        Returns:
            int: Digest size in bytes
        """
        return Ripemd160.DigestSize()

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/bip/utils/crypto/hash160.py`.

**Classes defined**: Hash160

**Functions defined**: QuickDigest, DigestSize

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 58
- Code lines: 27
- Comment lines: 27
- Blank lines: 4

### Main Components

**Classes** (1):
- `Hash160`

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
python python/ccxt/static_dependencies/bip/utils/crypto/hash160.py
```

