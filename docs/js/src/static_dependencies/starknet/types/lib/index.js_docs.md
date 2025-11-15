# Documentation: js/src/static_dependencies/starknet/types/lib/index.js

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/types/lib/index.js`
- **Size**: 2,025 bytes
- **Lines**: 47
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
export var TransactionType;
(function (TransactionType) {
    TransactionType["DECLARE"] = "DECLARE";
    TransactionType["DEPLOY"] = "DEPLOY";
    TransactionType["DEPLOY_ACCOUNT"] = "DEPLOY_ACCOUNT";
    TransactionType["INVOKE"] = "INVOKE_FUNCTION";
})(TransactionType || (TransactionType = {}));
/**
 * new statuses are defined by props: finality_status and execution_status
 * to be #deprecated
 */
export var TransactionStatus;
(function (TransactionStatus) {
    TransactionStatus["NOT_RECEIVED"] = "NOT_RECEIVED";
    TransactionStatus["RECEIVED"] = "RECEIVED";
    TransactionStatus["ACCEPTED_ON_L2"] = "ACCEPTED_ON_L2";
    TransactionStatus["ACCEPTED_ON_L1"] = "ACCEPTED_ON_L1";
    TransactionStatus["REJECTED"] = "REJECTED";
    TransactionStatus["REVERTED"] = "REVERTED";
})(TransactionStatus || (TransactionStatus = {}));
export var TransactionFinalityStatus;
(function (TransactionFinalityStatus) {
    TransactionFinalityStatus["NOT_RECEIVED"] = "NOT_RECEIVED";
    TransactionFinalityStatus["RECEIVED"] = "RECEIVED";
    TransactionFinalityStatus["ACCEPTED_ON_L2"] = "ACCEPTED_ON_L2";
    TransactionFinalityStatus["ACCEPTED_ON_L1"] = "ACCEPTED_ON_L1";
})(TransactionFinalityStatus || (TransactionFinalityStatus = {}));
export var TransactionExecutionStatus;
(function (TransactionExecutionStatus) {
    TransactionExecutionStatus["REJECTED"] = "REJECTED";
    TransactionExecutionStatus["REVERTED"] = "REVERTED";
    TransactionExecutionStatus["SUCCEEDED"] = "SUCCEEDED";
})(TransactionExecutionStatus || (TransactionExecutionStatus = {}));
export var BlockStatus;
(function (BlockStatus) {
    BlockStatus["PENDING"] = "PENDING";
    BlockStatus["ACCEPTED_ON_L1"] = "ACCEPTED_ON_L1";
    BlockStatus["ACCEPTED_ON_L2"] = "ACCEPTED_ON_L2";
    BlockStatus["REJECTED"] = "REJECTED";
})(BlockStatus || (BlockStatus = {}));
export var BlockTag;
(function (BlockTag) {
    BlockTag["pending"] = "pending";
    BlockTag["latest"] = "latest";
})(BlockTag || (BlockTag = {}));
export * from './contract/index.js';

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/starknet/types/lib/index.js`.

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 47
- Code lines: 46
- Comment lines: 4
- Blank lines: -3

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `./contract/index.js` (imported)
- `./contract/index.js` (referenced)



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/starknet/types/lib/index.js
```

