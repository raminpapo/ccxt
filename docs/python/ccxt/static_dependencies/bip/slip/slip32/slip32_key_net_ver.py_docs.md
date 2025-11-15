# Documentation: python/ccxt/static_dependencies/bip/slip/slip32/slip32_key_net_ver.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/bip/slip/slip32/slip32_key_net_ver.py`
- **Size**: 2,023 bytes
- **Lines**: 63
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

"""Module for SLIP32 net version class."""


class Slip32KeyNetVersions:
    """
    SLIP32 key net versions class.
    It represents a SLIP32 key net versions.
    """

    m_pub_net_ver: str
    m_priv_net_ver: str

    def __init__(self,
                 pub_net_ver: str,
                 priv_net_ver: str) -> None:
        """
        Construct class.

        Args:
            pub_net_ver (str) : Public net version
            priv_net_ver (str): Private net version
        """
        self.m_pub_net_ver = pub_net_ver
        self.m_priv_net_ver = priv_net_ver

    def Public(self) -> str:
        """
        Get public net version.

        Returns:
            str: Public net version
        """
        return self.m_pub_net_ver

    def Private(self) -> str:
        """
        Get private net version.

        Returns:
            str: Private net version
        """
        return self.m_priv_net_ver

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/bip/slip/slip32/slip32_key_net_ver.py`.

**Classes defined**: Slip32KeyNetVersions

**Functions defined**: Private, Public, __init__

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 63
- Code lines: 33
- Comment lines: 28
- Blank lines: 2

### Main Components

**Classes** (1):
- `Slip32KeyNetVersions`

**Functions** (3):
- `Private()`
- `Public()`
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
python python/ccxt/static_dependencies/bip/slip/slip32/slip32_key_net_ver.py
```

