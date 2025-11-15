# Documentation: python/ccxt/static_dependencies/bip/utils/misc/string.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/bip/utils/misc/string.py`
- **Size**: 1,830 bytes
- **Lines**: 55
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

"""Module with some string utility functions."""

# Imports
import unicodedata


class StringUtils:
    """Class container for string utility functions."""

    @staticmethod
    def NormalizeNfc(data_str: str) -> str:
        """
        Normalize string using NFC.

        Args:
            data_str (str): Input string

        Returns:
            str: Normalized string
        """
        return unicodedata.normalize("NFC", data_str)

    @staticmethod
    def NormalizeNfkd(data_str: str) -> str:
        """
        Normalize string using NFKD.

        Args:
            data_str (str): Input string

        Returns:
            str: Normalized string
        """
        return unicodedata.normalize("NFKD", data_str)

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/bip/utils/misc/string.py`.

**Classes defined**: StringUtils

**Functions defined**: NormalizeNfkd, NormalizeNfc

**Dependencies**: This file imports other modules.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 55
- Code lines: 24
- Comment lines: 26
- Blank lines: 5

### Main Components

**Classes** (1):
- `StringUtils`

**Functions** (2):
- `NormalizeNfc()`
- `NormalizeNfkd()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/bip/utils/misc/string.py
```

