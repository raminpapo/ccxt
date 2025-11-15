# Documentation: python/ccxt/static_dependencies/bip/ecc/curve/elliptic_curve_getter.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/bip/ecc/curve/elliptic_curve_getter.py`
- **Size**: 2,963 bytes
- **Lines**: 75
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

"""Module for getting elliptic curves classes."""

# Imports
from typing import Dict

from .elliptic_curve import EllipticCurve
from .elliptic_curve_types import EllipticCurveTypes
# from ..ed25519.ed25519 import Ed25519
# from ..ed25519_blake2b.ed25519_blake2b import Ed25519Blake2b
# from ..ed25519_kholaw.ed25519_kholaw import Ed25519Kholaw
# from ..ed25519_monero.ed25519_monero import Ed25519Monero
# from ..nist256p1.nist256p1 import Nist256p1
from ..secp256k1.secp256k1 import Secp256k1
# from ..sr25519.sr25519 import Sr25519


class EllipticCurveGetterConst:
    """Class container for elliptic curve getter constants."""

    # Elliptic curve type to instance
    TYPE_TO_INSTANCE: Dict[EllipticCurveTypes, EllipticCurve] = {
        # EllipticCurveTypes.ED25519: Ed25519,
        # EllipticCurveTypes.ED25519_BLAKE2B: Ed25519Blake2b,
        # EllipticCurveTypes.ED25519_KHOLAW: Ed25519Kholaw,
        # EllipticCurveTypes.ED25519_MONERO: Ed25519Monero,
        # EllipticCurveTypes.NIST256P1: Nist256p1,
        EllipticCurveTypes.SECP256K1: Secp256k1,
        # EllipticCurveTypes.SR25519: Sr25519,
    }


class EllipticCurveGetter:
    """
    Elliptic curve getter class.
    It allows to get the elliptic curve class from its type.
    """

    @staticmethod
    def FromType(curve_type: EllipticCurveTypes) -> EllipticCurve:
        """
        Get the elliptic curve class from its type.

        Args:
            curve_type (EllipticCurveTypes): Curve type

        Returns:
            EllipticCurve object: EllipticCurve object

        Raises:
            TypeError: If curve type is not a EllipticCurveTypes enum
        """
        if not isinstance(curve_type, EllipticCurveTypes):
            raise TypeError("Curve type is not an enumerative of EllipticCurveTypes")
        return EllipticCurveGetterConst.TYPE_TO_INSTANCE[curve_type]

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/bip/ecc/curve/elliptic_curve_getter.py`.

**Classes defined**: EllipticCurveGetterConst, from, EllipticCurveGetter

**Functions defined**: FromType

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 75
- Code lines: 29
- Comment lines: 39
- Blank lines: 7

### Main Components

**Classes** (2):
- `EllipticCurveGetter`
- `EllipticCurveGetterConst`

**Functions** (1):
- `FromType()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/bip/ecc/curve/elliptic_curve_getter.py
```

