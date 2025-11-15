# Documentation: js/src/base/errors.js

## File Metadata

- **Path**: `js/src/base/errors.js`
- **Size**: 7,381 bytes
- **Lines**: 250
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
/* eslint-disable max-classes-per-file */
class BaseError extends Error {
    constructor(message) {
        super(message);
        this.name = 'BaseError';
    }
}
class ExchangeError extends BaseError {
    constructor(message) {
        super(message);
        this.name = 'ExchangeError';
    }
}
class AuthenticationError extends ExchangeError {
    constructor(message) {
        super(message);
        this.name = 'AuthenticationError';
    }
}
class PermissionDenied extends AuthenticationError {
    constructor(message) {
        super(message);
        this.name = 'PermissionDenied';
    }
}
class AccountNotEnabled extends PermissionDenied {
    constructor(message) {
        super(message);
        this.name = 'AccountNotEnabled';
    }
}
class AccountSuspended extends AuthenticationError {
    constructor(message) {
        super(message);
        this.name = 'AccountSuspended';
    }
}
class ArgumentsRequired extends ExchangeError {
    constructor(message) {
        super(message);
        this.name = 'ArgumentsRequired';
    }
}
class BadRequest extends ExchangeError {
    constructor(message) {
        super(message);
        this.name = 'BadRequest';
    }
}
class BadSymbol extends BadRequest {
    constructor(message) {
        super(message);
        this.name = 'BadSymbol';
    }
}
class OperationRejected extends ExchangeError {
    constructor(message) {
        super(message);
        this.name = 'OperationRejected';
    }
}
class NoChange extends OperationRejected {
    constructor(message) {
        super(message);
        this.name = 'NoChange';
    }
}
class MarginModeAlreadySet extends NoChange {
    constructor(message) {
        super(message);
        this.name = 'MarginModeAlreadySet';
    }
}
class MarketClosed extends OperationRejected {
    constructor(message) {
        super(message);
        this.name = 'MarketClosed';
    }
}
class ManualInteractionNeeded extends OperationRejected {
    constructor(message) {
        super(message);
        this.name = 'ManualInteractionNeeded';
    }
}
class RestrictedLocation extends OperationRejected {
    constructor(message) {
        super(message);
        this.name = 'RestrictedLocation';
    }
}
class InsufficientFunds extends ExchangeError {
    constructor(message) {
        super(message);
        this.name = 'InsufficientFunds';
    }
}
class InvalidAddress extends ExchangeError {
    constructor(message) {
        super(message);
        this.name = 'InvalidAddress';
    }
}
class AddressPending extends InvalidAddress {
    constructor(message) {
        super(message);
        this.name = 'AddressPending';
    }
}
class InvalidOrder extends ExchangeError {
    constructor(message) {
        super(message);
        this.name = 'InvalidOrder';
    }
}
class OrderNotFound extends InvalidOrder {
    constructor(message) {
        super(message);
        this.name = 'OrderNotFound';
    }
}
class OrderNotCached extends InvalidOrder {
    constructor(message) {
        super(message);
        this.name = 'OrderNotCached';
    }
}
class OrderImmediatelyFillable extends InvalidOrder {
    constructor(message) {
        super(message);
        this.name = 'OrderImmediatelyFillable';
    }
}
class OrderNotFillable extends InvalidOrder {
    constructor(message) {
        super(message);
        this.name = 'OrderNotFillable';
    }
}
class DuplicateOrderId extends InvalidOrder {
    constructor(message) {
        super(message);
        this.name = 'DuplicateOrderId';
    }
}
class ContractUnavailable extends InvalidOrder {
    constructor(message) {
        super(message);
        this.name = 'ContractUnavailable';
    }
}
class NotSupported extends ExchangeError {
    constructor(message) {
        super(message);
        this.name = 'NotSupported';
    }
}
class InvalidProxySettings extends ExchangeError {
    constructor(message) {
        super(message);
        this.name = 'InvalidProxySettings';
    }
}
class ExchangeClosedByUser extends ExchangeError {
    constructor(message) {
        super(message);
        this.name = 'ExchangeClosedByUser';
    }
}
class OperationFailed extends BaseError {
    constructor(message) {
        super(message);
        this.name = 'OperationFailed';
    }
}
class NetworkError extends OperationFailed {
    constructor(message) {
        super(message);
        this.name = 'NetworkError';
    }
}
class DDoSProtection extends NetworkError {
    constructor(message) {
        super(message);
        this.name = 'DDoSProtection';
    }
}
class RateLimitExceeded extends NetworkError {
    constructor(message) {
        super(message);
        this.name = 'RateLimitExceeded';
    }
}
class ExchangeNotAvailable extends NetworkError {
    constructor(message) {
        super(message);
        this.name = 'ExchangeNotAvailable';
    }
}
class OnMaintenance extends ExchangeNotAvailable {
    constructor(message) {
        super(message);
        this.name = 'OnMaintenance';
    }
}
class InvalidNonce extends NetworkError {
    constructor(message) {
        super(message);
        this.name = 'InvalidNonce';
    }
}
class ChecksumError extends InvalidNonce {
    constructor(message) {
        super(message);
        this.name = 'ChecksumError';
    }
}
class RequestTimeout extends NetworkError {
    constructor(message) {
        super(message);
        this.name = 'RequestTimeout';
    }
}
class BadResponse extends OperationFailed {
    constructor(message) {
        super(message);
        this.name = 'BadResponse';
    }
}
class NullResponse extends BadResponse {
    constructor(message) {
        super(message);
        this.name = 'NullResponse';
    }
}
class CancelPending extends OperationFailed {
    constructor(message) {
        super(message);
        this.name = 'CancelPending';
    }
}
class UnsubscribeError extends BaseError {
    constructor(message) {
        super(message);
        this.name = 'UnsubscribeError';
    }
}
export { BaseError, ExchangeError, AuthenticationError, PermissionDenied, AccountNotEnabled, AccountSuspended, ArgumentsRequired, BadRequest, BadSymbol, OperationRejected, NoChange, MarginModeAlreadySet, MarketClosed, ManualInteractionNeeded, RestrictedLocation, InsufficientFunds, InvalidAddress, AddressPending, InvalidOrder, OrderNotFound, OrderNotCached, OrderImmediatelyFillable, OrderNotFillable, DuplicateOrderId, ContractUnavailable, NotSupported, InvalidProxySettings, ExchangeClosedByUser, OperationFailed, NetworkError, DDoSProtection, RateLimitExceeded, ExchangeNotAvailable, OnMaintenance, InvalidNonce, ChecksumError, RequestTimeout, BadResponse, NullResponse, CancelPending, UnsubscribeError };
export default { BaseError, ExchangeError, AuthenticationError, PermissionDenied, AccountNotEnabled, AccountSuspended, ArgumentsRequired, BadRequest, BadSymbol, OperationRejected, NoChange, MarginModeAlreadySet, MarketClosed, ManualInteractionNeeded, RestrictedLocation, InsufficientFunds, InvalidAddress, AddressPending, InvalidOrder, OrderNotFound, OrderNotCached, OrderImmediatelyFillable, OrderNotFillable, DuplicateOrderId, ContractUnavailable, NotSupported, InvalidProxySettings, ExchangeClosedByUser, OperationFailed, NetworkError, DDoSProtection, RateLimitExceeded, ExchangeNotAvailable, OnMaintenance, InvalidNonce, ChecksumError, RequestTimeout, BadResponse, NullResponse, CancelPending, UnsubscribeError };

```

## High-Level Overview

This is a JavaScript file located at `js/src/base/errors.js`.

**Classes defined**: ArgumentsRequired, OperationRejected, PermissionDenied, BadSymbol, ExchangeError, AccountNotEnabled, BadRequest, BaseError, AccountSuspended, AuthenticationError

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 250
- Code lines: 249
- Comment lines: 1
- Blank lines: 0

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
node js/src/base/errors.js
```

