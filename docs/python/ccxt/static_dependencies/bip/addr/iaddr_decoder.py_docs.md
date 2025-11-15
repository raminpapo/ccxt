# Documentation: python/ccxt/static_dependencies/bip/addr/iaddr_decoder.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/bip/addr/iaddr_decoder.py`
- **Size**: 1,833 bytes
- **Lines**: 49
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

"""Module with interface for address encoding classes."""

# Imports
from abc import ABC, abstractmethod
from typing import Any


class IAddrDecoder(ABC):
    """Address decoder interface."""

    @staticmethod
    @abstractmethod
    def DecodeAddr(addr: str,
                   **kwargs: Any) -> bytes:
        """
        Decode an address to bytes.
        Depending on the coin, the result can be a public key or a public key hash bytes.

        Args:
            addr (str): Address string
            **kwargs  : Arbitrary arguments depending on the address type

        Returns:
            bytes: Public key bytes or public key hash

        Raises:
            ValueError: If the address encoding is not valid
        """

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/bip/addr/iaddr_decoder.py`.

**Classes defined**: IAddrDecoder

**Functions defined**: DecodeAddr

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 49
- Code lines: 20
- Comment lines: 26
- Blank lines: 3

### Main Components

**Classes** (1):
- `IAddrDecoder`

**Functions** (1):
- `DecodeAddr()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/bip/addr/iaddr_decoder.py
```

