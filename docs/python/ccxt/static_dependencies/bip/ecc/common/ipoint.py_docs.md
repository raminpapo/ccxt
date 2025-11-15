# Documentation: python/ccxt/static_dependencies/bip/ecc/common/ipoint.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/bip/ecc/common/ipoint.py`
- **Size**: 4,610 bytes
- **Lines**: 191
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

"""Module with interfaces for point classes."""

# Imports
from __future__ import annotations

from abc import ABC, abstractmethod
from typing import Any

from ..curve.elliptic_curve_types import EllipticCurveTypes
from ...utils.misc import DataBytes


class IPoint(ABC):
    """Interface for a generic elliptic curve point."""

    @classmethod
    @abstractmethod
    def FromBytes(cls,
                  point_bytes: bytes) -> IPoint:
        """
        Construct class from point bytes.

        Args:
            point_bytes (bytes): Point bytes

        Returns:
            IPoint: IPoint object
        """

    @classmethod
    @abstractmethod
    def FromCoordinates(cls,
                        x: int,
                        y: int) -> IPoint:
        """
        Construct class from point coordinates.

        Args:
            x (int): X coordinate of the point
            y (int): Y coordinate of the point

        Returns:
            IPoint: IPoint object
        """

    @staticmethod
    @abstractmethod
    def CurveType() -> EllipticCurveTypes:
        """
        Get the elliptic curve type.

        Returns:
           EllipticCurveTypes: Elliptic curve type
        """

    @staticmethod
    @abstractmethod
    def CoordinateLength() -> int:
        """
        Get the coordinate length.

        Returns:
           int: Coordinate key length
        """

    @abstractmethod
    def UnderlyingObject(self) -> Any:
        """
        Get the underlying object.

        Returns:
           Any: Underlying object
        """

    @abstractmethod
    def X(self) -> int:
        """
        Return X coordinate of the point.

        Returns:
            int: X coordinate of the point
        """

    @abstractmethod
    def Y(self) -> int:
        """
        Return Y coordinate of the point.

        Returns:
            int: Y coordinate of the point
        """

    @abstractmethod
    def Raw(self) -> DataBytes:
        """
        Return the point raw bytes.

        Returns:
            DataBytes object: DataBytes object
        """

    @abstractmethod
    def RawEncoded(self) -> DataBytes:
        """
        Return the encoded point raw bytes.

        Returns:
            DataBytes object: DataBytes object
        """

    @abstractmethod
    def RawDecoded(self) -> DataBytes:
        """
        Return the decoded point raw bytes.

        Returns:
            DataBytes object: DataBytes object
        """

    @abstractmethod
    def __add__(self,
                point: IPoint) -> IPoint:
        """
        Add point to another point.

        Args:
            point (IPoint object): IPoint object

        Returns:
            IPoint object: IPoint object
        """

    @abstractmethod
    def __radd__(self,
                 point: IPoint) -> IPoint:
        """
        Add point to another point.

        Args:
            point (IPoint object): IPoint object

        Returns:
            IPoint object: IPoint object
        """

    @abstractmethod
    def __mul__(self,
                scalar: int) -> IPoint:
        """
        Multiply point by a scalar.

        Args:
            scalar (int): scalar

        Returns:
            IPoint object: IPoint object
        """

    @abstractmethod
    def __rmul__(self,
                 scalar: int) -> IPoint:
        """
        Multiply point by a scalar.

        Args:
            scalar (int): scalar

        Returns:
            IPoint object: IPoint object
        """

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/bip/ecc/common/ipoint.py`.

**Classes defined**: from, IPoint

**Functions defined**: RawEncoded, CurveType, Y, UnderlyingObject, CoordinateLength, FromCoordinates, Raw, FromBytes, RawDecoded, X

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 191
- Code lines: 130
- Comment lines: 50
- Blank lines: 11

### Main Components

**Classes** (1):
- `IPoint`

**Functions** (14):
- `CoordinateLength()`
- `CurveType()`
- `FromBytes()`
- `FromCoordinates()`
- `Raw()`
- `RawDecoded()`
- `RawEncoded()`
- `UnderlyingObject()`
- `X()`
- `Y()`
- `__add__()`
- `__mul__()`
- `__radd__()`
- `__rmul__()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/bip/ecc/common/ipoint.py
```

