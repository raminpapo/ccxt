# Documentation: python/ccxt/static_dependencies/msgpack/_cmsgpack.pyx

## File Metadata

- **Path**: `python/ccxt/static_dependencies/msgpack/_cmsgpack.pyx`
- **Size**: 335 bytes
- **Lines**: 12
- **Type**: Unknown
- **Extension**: .pyx


## Original Source Code

```
# coding: utf-8
#cython: embedsignature=True, c_string_encoding=ascii, language_level=3
from cpython.datetime cimport import_datetime, datetime_new
import_datetime()

import datetime
cdef object utc = datetime.timezone.utc
cdef object epoch = datetime_new(1970, 1, 1, 0, 0, 0, 0, tz=utc)

include "_packer.pyx"
include "_unpacker.pyx"

```

## High-Level Overview

This is a Unknown file located at `python/ccxt/static_dependencies/msgpack/_cmsgpack.pyx`.

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 12
- Code lines: 7
- Comment lines: 2
- Blank lines: 3

### Main Components

**Functions** (1):
- `object()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Unknown file:**

