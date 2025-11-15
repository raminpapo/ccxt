# Documentation: python/ccxt/static_dependencies/bip/ecc/curve/elliptic_curve_types.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/bip/ecc/curve/elliptic_curve_types.py`
- **Size**: 1,449 bytes
- **Lines**: 38
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

"""Module for elliptic curves enum."""

# Imports
from enum import Enum, auto, unique


@unique
class EllipticCurveTypes(Enum):
    """Enumerative for elliptic curve types."""

    ED25519 = auto()
    ED25519_BLAKE2B = auto()
    ED25519_KHOLAW = auto()
    ED25519_MONERO = auto()
    NIST256P1 = auto()
    SECP256K1 = auto()
    SR25519 = auto()

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/bip/ecc/curve/elliptic_curve_types.py`.

**Classes defined**: EllipticCurveTypes

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 38
- Code lines: 12
- Comment lines: 22
- Blank lines: 4

### Main Components

**Classes** (1):
- `EllipticCurveTypes`

**Constants** (7):
- `ED25519`
- `ED25519_BLAKE2B`
- `ED25519_KHOLAW`
- `ED25519_MONERO`
- `NIST256P1`
- `SECP256K1`
- `SR25519`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/bip/ecc/curve/elliptic_curve_types.py
```

