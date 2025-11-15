# Documentation: python/ccxt/base/errors.py

## File Metadata

- **Path**: `python/ccxt/base/errors.py`
- **Size**: 4,734 bytes
- **Lines**: 268
- **Type**: Python
- **Extension**: .py


## Original Source Code

```python
error_hierarchy = {
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
}


class BaseError(Exception):
    pass


class ExchangeError(BaseError):
    pass


class AuthenticationError(ExchangeError):
    pass


class PermissionDenied(AuthenticationError):
    pass


class AccountNotEnabled(PermissionDenied):
    pass


class AccountSuspended(AuthenticationError):
    pass


class ArgumentsRequired(ExchangeError):
    pass


class BadRequest(ExchangeError):
    pass


class BadSymbol(BadRequest):
    pass


class OperationRejected(ExchangeError):
    pass


class NoChange(OperationRejected):
    pass


class MarginModeAlreadySet(NoChange):
    pass


class MarketClosed(OperationRejected):
    pass


class ManualInteractionNeeded(OperationRejected):
    pass


class RestrictedLocation(OperationRejected):
    pass


class InsufficientFunds(ExchangeError):
    pass


class InvalidAddress(ExchangeError):
    pass


class AddressPending(InvalidAddress):
    pass


class InvalidOrder(ExchangeError):
    pass


class OrderNotFound(InvalidOrder):
    pass


class OrderNotCached(InvalidOrder):
    pass


class OrderImmediatelyFillable(InvalidOrder):
    pass


class OrderNotFillable(InvalidOrder):
    pass


class DuplicateOrderId(InvalidOrder):
    pass


class ContractUnavailable(InvalidOrder):
    pass


class NotSupported(ExchangeError):
    pass


class InvalidProxySettings(ExchangeError):
    pass


class ExchangeClosedByUser(ExchangeError):
    pass


class OperationFailed(BaseError):
    pass


class NetworkError(OperationFailed):
    pass


class DDoSProtection(NetworkError):
    pass


class RateLimitExceeded(NetworkError):
    pass


class ExchangeNotAvailable(NetworkError):
    pass


class OnMaintenance(ExchangeNotAvailable):
    pass


class InvalidNonce(NetworkError):
    pass


class ChecksumError(InvalidNonce):
    pass


class RequestTimeout(NetworkError):
    pass


class BadResponse(OperationFailed):
    pass


class NullResponse(BadResponse):
    pass


class CancelPending(OperationFailed):
    pass


class UnsubscribeError(BaseError):
    pass


__all__ = [
    'error_hierarchy',
    'BaseError',
    'ExchangeError',
    'AuthenticationError',
    'PermissionDenied',
    'AccountNotEnabled',
    'AccountSuspended',
    'ArgumentsRequired',
    'BadRequest',
    'BadSymbol',
    'OperationRejected',
    'NoChange',
    'MarginModeAlreadySet',
    'MarketClosed',
    'ManualInteractionNeeded',
    'RestrictedLocation',
    'InsufficientFunds',
    'InvalidAddress',
    'AddressPending',
    'InvalidOrder',
    'OrderNotFound',
    'OrderNotCached',
    'OrderImmediatelyFillable',
    'OrderNotFillable',
    'DuplicateOrderId',
    'ContractUnavailable',
    'NotSupported',
    'InvalidProxySettings',
    'ExchangeClosedByUser',
    'OperationFailed',
    'NetworkError',
    'DDoSProtection',
    'RateLimitExceeded',
    'ExchangeNotAvailable',
    'OnMaintenance',
    'InvalidNonce',
    'ChecksumError',
    'RequestTimeout',
    'BadResponse',
    'NullResponse',
    'CancelPending',
    'UnsubscribeError'
]

```

## High-Level Overview

This is a Python file located at `python/ccxt/base/errors.py`.

**Classes defined**: ArgumentsRequired, OperationRejected, PermissionDenied, BadSymbol, ExchangeError, AccountNotEnabled, BadRequest, BaseError, AccountSuspended, AuthenticationError



## Detailed Walkthrough

### Code Structure

- Total lines: 268
- Code lines: 183
- Comment lines: 0
- Blank lines: 85

### Main Components

**Classes** (41):
- `AccountNotEnabled`
- `AccountSuspended`
- `AddressPending`
- `ArgumentsRequired`
- `AuthenticationError`
- `BadRequest`
- `BadResponse`
- `BadSymbol`
- `BaseError`
- `CancelPending`
- `ChecksumError`
- `ContractUnavailable`
- `DDoSProtection`
- `DuplicateOrderId`
- `ExchangeClosedByUser`
- `ExchangeError`
- `ExchangeNotAvailable`
- `InsufficientFunds`
- `InvalidAddress`
- `InvalidNonce`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Implements caching mechanisms



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this Python file:**

```bash
python python/ccxt/base/errors.py
```

