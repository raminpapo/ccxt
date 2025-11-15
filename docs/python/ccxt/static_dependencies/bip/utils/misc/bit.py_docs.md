# Documentation: python/ccxt/static_dependencies/bip/utils/misc/bit.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/bip/utils/misc/bit.py`
- **Size**: 3,314 bytes
- **Lines**: 116
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

"""Module with some bits utility functions."""


class BitUtils:
    """Class container for bit utility functions."""

    @staticmethod
    def IsBitSet(value: int,
                 bit_num: int) -> bool:
        """
        Get if the specified bit is set.

        Args:
            value (int)  : Value
            bit_num (int): Bit number to check

        Returns:
            bool: True if bit is set, false otherwise
        """
        return (value & (1 << bit_num)) != 0

    @staticmethod
    def AreBitsSet(value: int,
                   bit_mask: int) -> bool:
        """
        Get if the specified bits are set.

        Args:
            value (int)   : Value
            bit_mask (int): Bit mask to check

        Returns:
            bool: True if bit is set, false otherwise
        """
        return (value & bit_mask) != 0

    @staticmethod
    def SetBit(value: int,
               bit_num: int) -> int:
        """
        Set the specified bit.

        Args:
            value (int)  : Value
            bit_num (int): Bit number to set

        Returns:
            int: Value with the specified bit set
        """
        return value | (1 << bit_num)

    @staticmethod
    def SetBits(value: int,
                bit_mask: int) -> int:
        """
        Set the specified bits.

        Args:
            value (int)   : Value
            bit_mask (int): Bit mask to set

        Returns:
            int: Value with the specified bit set
        """
        return value | bit_mask

    @staticmethod
    def ResetBit(value: int,
                 bit_num: int) -> int:
        """
        Reset the specified bit.

        Args:
            value (int)  : Value
            bit_num (int): Bit number to reset

        Returns:
            int: Value with the specified bit reset
        """
        return value & ~(1 << bit_num)

    @staticmethod
    def ResetBits(value: int,
                  bit_mask: int) -> int:
        """
        Reset the specified bits.

        Args:
            value (int)   : Value
            bit_mask (int): Bit mask to reset

        Returns:
            int: Value with the specified bit reset
        """
        return value & ~bit_mask

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/bip/utils/misc/bit.py`.

**Classes defined**: BitUtils

**Functions defined**: SetBit, ResetBit, ResetBits, IsBitSet, SetBits, AreBitsSet

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 116
- Code lines: 75
- Comment lines: 33
- Blank lines: 8

### Main Components

**Classes** (1):
- `BitUtils`

**Functions** (6):
- `AreBitsSet()`
- `IsBitSet()`
- `ResetBit()`
- `ResetBits()`
- `SetBit()`
- `SetBits()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/bip/utils/misc/bit.py
```

