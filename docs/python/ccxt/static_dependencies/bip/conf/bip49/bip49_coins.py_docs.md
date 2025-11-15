# Documentation: python/ccxt/static_dependencies/bip/conf/bip49/bip49_coins.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/bip/conf/bip49/bip49_coins.py`
- **Size**: 1,831 bytes
- **Lines**: 54
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

"""Module for BIP49 coins enum."""

# Imports
from enum import auto, unique

from .bip_coins import BipCoins


@unique
class Bip49Coins(BipCoins):
    """Enumerative for supported BIP49 coins."""

    # Main nets
    BITCOIN = auto()
    BITCOIN_CASH = auto()
    BITCOIN_CASH_SLP = auto()
    BITCOIN_SV = auto()
    DASH = auto()
    DOGECOIN = auto()
    ECASH = auto()
    LITECOIN = auto()
    ZCASH = auto()
    # Test nets
    BITCOIN_CASH_TESTNET = auto()
    BITCOIN_CASH_SLP_TESTNET = auto()
    BITCOIN_SV_TESTNET = auto()
    BITCOIN_REGTEST = auto()
    BITCOIN_TESTNET = auto()
    DASH_TESTNET = auto()
    DOGECOIN_TESTNET = auto()
    ECASH_TESTNET = auto()
    LITECOIN_TESTNET = auto()
    ZCASH_TESTNET = auto()

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/bip/conf/bip49/bip49_coins.py`.

**Classes defined**: Bip49Coins

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 54
- Code lines: 25
- Comment lines: 24
- Blank lines: 5

### Main Components

**Classes** (1):
- `Bip49Coins`

**Constants** (19):
- `BITCOIN`
- `BITCOIN_CASH`
- `BITCOIN_CASH_SLP`
- `BITCOIN_CASH_SLP_TESTNET`
- `BITCOIN_CASH_TESTNET`
- `BITCOIN_REGTEST`
- `BITCOIN_SV`
- `BITCOIN_SV_TESTNET`
- `BITCOIN_TESTNET`
- `DASH`
- `DASH_TESTNET`
- `DOGECOIN`
- `DOGECOIN_TESTNET`
- `ECASH`
- `ECASH_TESTNET`
- `LITECOIN`
- `LITECOIN_TESTNET`
- `ZCASH`
- `ZCASH_TESTNET`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/bip/conf/bip49/bip49_coins.py
```

