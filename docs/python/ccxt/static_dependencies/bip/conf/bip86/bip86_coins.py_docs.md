# Documentation: python/ccxt/static_dependencies/bip/conf/bip86/bip86_coins.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/bip/conf/bip86/bip86_coins.py`
- **Size**: 1,407 bytes
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

"""Module for BIP86 coins enum."""

# Imports
from enum import auto, unique

from .bip_coins import BipCoins


@unique
class Bip86Coins(BipCoins):
    """Enumerative for supported BIP86 coins."""

    # Main nets
    BITCOIN = auto()
    # Test nets
    BITCOIN_REGTEST = auto()
    BITCOIN_TESTNET = auto()

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/bip/conf/bip86/bip86_coins.py`.

**Classes defined**: Bip86Coins

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 38
- Code lines: 9
- Comment lines: 24
- Blank lines: 5

### Main Components

**Classes** (1):
- `Bip86Coins`

**Constants** (3):
- `BITCOIN`
- `BITCOIN_REGTEST`
- `BITCOIN_TESTNET`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/bip/conf/bip86/bip86_coins.py
```

