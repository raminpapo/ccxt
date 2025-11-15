# Documentation: js/src/base/errorHierarchy.js

## File Metadata

- **Path**: `js/src/base/errorHierarchy.js`
- **Size**: 1,770 bytes
- **Lines**: 59
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
const errorHierarchy = {
    'BaseError': {
        'ExchangeError': {
            'AuthenticationError': {
                'PermissionDenied': {
                    'AccountNotEnabled': {},
                },
                'AccountSuspended': {},
            },
            'ArgumentsRequired': {},
            'BadRequest': {
                'BadSymbol': {},
            },
            'OperationRejected': {
                'NoChange': {
                    'MarginModeAlreadySet': {},
                },
                'MarketClosed': {},
                'ManualInteractionNeeded': {},
                'RestrictedLocation': {},
            },
            'InsufficientFunds': {},
            'InvalidAddress': {
                'AddressPending': {},
            },
            'InvalidOrder': {
                'OrderNotFound': {},
                'OrderNotCached': {},
                'OrderImmediatelyFillable': {},
                'OrderNotFillable': {},
                'DuplicateOrderId': {},
                'ContractUnavailable': {},
            },
            'NotSupported': {},
            'InvalidProxySettings': {},
            'ExchangeClosedByUser': {},
        },
        'OperationFailed': {
            'NetworkError': {
                'DDoSProtection': {},
                'RateLimitExceeded': {},
                'ExchangeNotAvailable': {
                    'OnMaintenance': {},
                },
                'InvalidNonce': {
                    'ChecksumError': {},
                },
                'RequestTimeout': {},
            },
            'BadResponse': {
                'NullResponse': {},
            },
            'CancelPending': {},
        },
        'UnsubscribeError': {},
    },
};
export default errorHierarchy;

```

## High-Level Overview

This is a JavaScript file located at `js/src/base/errorHierarchy.js`.



## Detailed Walkthrough

### Code Structure

- Total lines: 59
- Code lines: 58
- Comment lines: 0
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Implements caching mechanisms



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/base/errorHierarchy.js
```

