# Documentation: python/ccxt/static_dependencies/bip/utils/crypto/scrypt.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/bip/utils/crypto/scrypt.py`
- **Size**: 2,481 bytes
- **Lines**: 67
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

"""Module for Scrypt algorithm."""

# Imports
from typing import Union

from Crypto.Protocol.KDF import scrypt

from ..misc import AlgoUtils


class Scrypt:
    """
    Scrypt class.
    It derives key using Scrypt algorithm.
    """

    @staticmethod
    def DeriveKey(password: Union[bytes, str],  # pylint: disable=too-many-arguments
                  salt: Union[bytes, str],
                  key_len: int,
                  n: int,
                  r: int,
                  p: int) -> bytes:
        """
        Derive a key.

        Args:
            password (str or bytes): Password
            salt (str or bytes)    : Salt
            key_len (int)          : Length of the derived key
            n (int)                : CPU/Memory cost parameter
            r (int)                : Block size parameter
            p (int)                : Parallelization parameter

        Returns:
            bytes: Computed result
        """

        # Type for password and salt should be Union[bytes, str] in pycryptodome, but it's only str
        # So, we ignore the mypy warning
        return scrypt(AlgoUtils.Encode(password),   # type: ignore [arg-type, return-value]
                      AlgoUtils.Encode(salt),       # type: ignore [arg-type]
                      key_len=key_len,
                      N=n,
                      r=r,
                      p=p)

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/bip/utils/crypto/scrypt.py`.

**Classes defined**: Scrypt

**Functions defined**: DeriveKey

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 67
- Code lines: 34
- Comment lines: 27
- Blank lines: 6

### Main Components

**Classes** (1):
- `Scrypt`

**Functions** (1):
- `DeriveKey()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/bip/utils/crypto/scrypt.py
```

