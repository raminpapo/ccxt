# Documentation: python/ccxt/static_dependencies/bip/conf/bip84/bip84_conf_getter.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/bip/conf/bip84/bip84_conf_getter.py`
- **Size**: 2,514 bytes
- **Lines**: 67
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

"""Module for getting BIP84 coins configuration."""

# Imports
from typing import Dict

from bip_utils.bip.conf.bip84.bip84_coins import Bip84Coins
from bip_utils.bip.conf.bip84.bip84_conf import Bip84Conf
from  import BipCoinConf, BipCoins


class Bip84ConfGetterConst:
    """Class container for BIP84 configuration getter constants."""

    # Map from Bip84Coins to configuration classes
    COIN_TO_CONF: Dict[BipCoins, BipCoinConf] = {
        Bip84Coins.BITCOIN: Bip84Conf.BitcoinMainNet,
        Bip84Coins.BITCOIN_REGTEST: Bip84Conf.BitcoinRegTest,
        Bip84Coins.BITCOIN_TESTNET: Bip84Conf.BitcoinTestNet,
        Bip84Coins.LITECOIN: Bip84Conf.LitecoinMainNet,
        Bip84Coins.LITECOIN_TESTNET: Bip84Conf.LitecoinTestNet,
    }


class Bip84ConfGetter:
    """
    BIP84 configuration getter class.
    It allows to get the BIP84 configuration of a specific coin.
    """

    @staticmethod
    def GetConfig(coin_type: BipCoins) -> BipCoinConf:
        """
        Get coin configuration.

        Args:
            coin_type (BipCoins): Coin type

        Returns:
            BipCoinConf: Coin configuration

        Raises:
            TypeError: If coin type is not of a Bip84Coins enumerative
        """
        if not isinstance(coin_type, Bip84Coins):
            raise TypeError("Coin type is not an enumerative of Bip84Coins")
        return Bip84ConfGetterConst.COIN_TO_CONF[coin_type]

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/bip/conf/bip84/bip84_conf_getter.py`.

**Classes defined**: Bip84ConfGetterConst, Bip84ConfGetter

**Functions defined**: GetConfig

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 67
- Code lines: 33
- Comment lines: 27
- Blank lines: 7

### Main Components

**Classes** (2):
- `Bip84ConfGetter`
- `Bip84ConfGetterConst`

**Functions** (1):
- `GetConfig()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/bip/conf/bip84/bip84_conf_getter.py
```

