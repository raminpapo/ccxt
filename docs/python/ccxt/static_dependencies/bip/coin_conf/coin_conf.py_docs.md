# Documentation: python/ccxt/static_dependencies/bip/coin_conf/coin_conf.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/bip/coin_conf/coin_conf.py`
- **Size**: 2,182 bytes
- **Lines**: 69
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

"""Module with helper class for generic coins configuration handling."""

# Imports
from typing import Any, Dict

from ..utils.conf import CoinNames as ConfCoinNames


class CoinConf:
    """Coin configuration class."""

    m_coin_name: ConfCoinNames
    m_params: Dict[str, Any]

    def __init__(self,
                 coin_name: ConfCoinNames,
                 params: Dict[str, Any]) -> None:
        """
        Construct class.

        Args:
            coin_name (CoinNames object): Coin names
            params (dict)               : SS58 format
        """
        self.m_coin_name = coin_name
        self.m_params = params

    def CoinNames(self) -> ConfCoinNames:
        """
        Get coin names.

        Returns:
            CoinNames object: CoinNames object
        """
        return self.m_coin_name

    def ParamByKey(self,
                   key: str) -> Any:
        """
        Get the parameter by key.

        Args:
            key (str): Parameter key

        Returns:
            Any: Parameter value
        """
        return self.m_params[key]

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/bip/coin_conf/coin_conf.py`.

**Classes defined**: for, CoinConf

**Functions defined**: __init__, CoinNames, ParamByKey

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 69
- Code lines: 35
- Comment lines: 28
- Blank lines: 6

### Main Components

**Classes** (1):
- `CoinConf`

**Functions** (3):
- `CoinNames()`
- `ParamByKey()`
- `__init__()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/bip/coin_conf/coin_conf.py
```

