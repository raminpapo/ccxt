# Documentation: python/ccxt/async_support/base/ws/functions.py

## File Metadata

- **Path**: `python/ccxt/async_support/base/ws/functions.py`
- **Size**: 1,499 bytes
- **Lines**: 60
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
# -*- coding: utf-8 -*-

from zlib import decompress, MAX_WBITS
from base64 import b64decode
from gzip import GzipFile
from io import BytesIO
import time
import datetime


def inflate(data):
    return decompress(data, -MAX_WBITS)


def inflate64(data):
    return inflate(b64decode(data))


def gunzip(data):
    return GzipFile('', 'rb', 9, BytesIO(data)).read().decode('utf-8')


#  Tmp : added methods below to avoid circular imports between exchange.py and aiohttp.py

def milliseconds():
    return int(time.time() * 1000)


def iso8601(timestamp=None):
    if timestamp is None:
        return timestamp
    if not isinstance(timestamp, int):
        return None
    if int(timestamp) < 0:
        return None
    try:
        utc = datetime.datetime.fromtimestamp(timestamp // 1000, datetime.timezone.utc)
        return utc.strftime('%Y-%m-%dT%H:%M:%S.%f')[:-6] + "{:03d}".format(int(timestamp) % 1000) + 'Z'
    except (TypeError, OverflowError, OSError):
        return None


def is_json_encoded_object(input):
    return (isinstance(input, str) and
            (len(input) >= 2) and
            ((input[0] == '{') or (input[0] == '[')))


def deep_extend(*args):
    result = None
    for arg in args:
        if isinstance(arg, dict):
            if not isinstance(result, dict):
                result = {}
            for key in arg:
                result[key] = deep_extend(result[key] if key in result else None, arg[key])
        else:
            result = arg
    return result

```

## High-Level Overview

This is a Python file located at `python/ccxt/async_support/base/ws/functions.py`.

**Functions defined**: milliseconds, is_json_encoded_object, iso8601, gunzip, inflate, deep_extend, inflate64

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 60
- Code lines: 41
- Comment lines: 2
- Blank lines: 17

### Main Components

**Functions** (7):
- `deep_extend()`
- `gunzip()`
- `inflate()`
- `inflate64()`
- `is_json_encoded_object()`
- `iso8601()`
- `milliseconds()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/async_support/base/ws/functions.py
```

