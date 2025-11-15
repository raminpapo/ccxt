# Documentation: python/ccxt/static_dependencies/dydx_v4_client/registry.py

## File Metadata

- **Path**: `python/ccxt/static_dependencies/dydx_v4_client/registry.py`
- **Size**: 1,248 bytes
- **Lines**: 39
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
from google.protobuf.json_format import ParseDict
from google.protobuf.any_pb2 import Any
from .dydxprotocol.sending.transfer_pb2 import (
    MsgDepositToSubaccount,
    MsgWithdrawFromSubaccount,
)
from .dydxprotocol.sending.tx_pb2 import MsgCreateTransfer
from .dydxprotocol.clob.tx_pb2 import (
    MsgPlaceOrder,
    MsgCancelOrder,
    MsgBatchCancel,
)
from .dydxprotocol.accountplus.tx_pb2 import TxExtension
from .cosmos.crypto.secp256k1.keys_pb2 import PubKey

registry = {
  '/dydxprotocol.clob.MsgPlaceOrder': MsgPlaceOrder,
  '/dydxprotocol.clob.MsgCancelOrder': MsgCancelOrder,
  '/dydxprotocol.clob.MsgBatchCancel': MsgBatchCancel,


  '/dydxprotocol.sending.MsgCreateTransfer': MsgCreateTransfer,
  '/dydxprotocol.sending.MsgWithdrawFromSubaccount': MsgWithdrawFromSubaccount,
  '/dydxprotocol.sending.MsgDepositToSubaccount': MsgDepositToSubaccount,
  '/dydxprotocol.accountplus.TxExtension': TxExtension,
  '/cosmos.crypto.secp256k1.PubKey': PubKey,
}

def encode_as_any(encodeObject):
    typeUrl = encodeObject['typeUrl']
    value = encodeObject['value']
    t = registry[typeUrl]
    message = ParseDict(value, t())
    packed = Any(
        type_url=typeUrl,
        value=message.SerializeToString()
    )
    return packed

```

## High-Level Overview

This is a Python file located at `python/ccxt/static_dependencies/dydx_v4_client/registry.py`.

**Functions defined**: encode_as_any

**Dependencies**: This file imports other modules.



## Detailed Walkthrough

### Code Structure

- Total lines: 39
- Code lines: 34
- Comment lines: 0
- Blank lines: 5

### Main Components

**Functions** (1):
- `encode_as_any()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/static_dependencies/dydx_v4_client/registry.py
```

