# Documentation: python/ccxt/static_dependencies/starknet/utils/schema.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/starknet/utils/schema.py`
- **Size**: 361 bytes
- **Lines**: 14
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
import os

from ..marshmallow import EXCLUDE, RAISE
from ..marshmallow import Schema as MarshmallowSchema

MARSHMALLOW_UKNOWN_EXCLUDE = os.environ.get("STARKNET_PY_MARSHMALLOW_UKNOWN_EXCLUDE")


class Schema(MarshmallowSchema):
    class Meta:
        unknown = (
            EXCLUDE if (MARSHMALLOW_UKNOWN_EXCLUDE or "").lower() == "true" else RAISE
        )

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/starknet/utils/schema.py`.

**Classes defined**: Meta, Schema

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 14
- Code lines: 9
- Comment lines: 0
- Blank lines: 5

### Main Components

**Classes** (2):
- `Meta`
- `Schema`

**Constants** (1):
- `MARSHMALLOW_UKNOWN_EXCLUDE`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/starknet/utils/schema.py
```

