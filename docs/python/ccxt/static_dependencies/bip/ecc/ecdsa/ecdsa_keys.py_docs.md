# Documentation: python/ccxt/static_dependencies/bip/ecc/ecdsa/ecdsa_keys.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/bip/ecc/ecdsa/ecdsa_keys.py`
- **Size**: 1,623 bytes
- **Lines**: 37
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

"""Module with some ECDSA keys constants."""


class EcdsaKeysConst:
    """Class container for ECDSA keys constants."""

    # Point coordinate length in bytes
    POINT_COORD_BYTE_LEN: int = 32
    # Private key length in bytes
    PRIV_KEY_BYTE_LEN: int = 32
    # Uncompressed public key prefix
    PUB_KEY_UNCOMPRESSED_PREFIX: bytes = b"\x04"
    # Compressed public key length in bytes
    PUB_KEY_COMPRESSED_BYTE_LEN: int = 33
    # Uncompressed public key length in bytes
    PUB_KEY_UNCOMPRESSED_BYTE_LEN: int = 65

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/bip/ecc/ecdsa/ecdsa_keys.py`.

**Classes defined**: EcdsaKeysConst

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 37
- Code lines: 8
- Comment lines: 26
- Blank lines: 3

### Main Components

**Classes** (1):
- `EcdsaKeysConst`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/bip/ecc/ecdsa/ecdsa_keys.py
```

