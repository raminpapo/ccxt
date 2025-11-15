# Documentation: js/src/static_dependencies/starknet/types/calldata.js

## File Metadata

- **Path**: `js/src/static_dependencies/starknet/types/calldata.js`
- **Size**: 855 bytes
- **Lines**: 23
- **Type**: JavaScript
- **Extension**: .js


## Original Source Code

```javascript
export var ValidateType;
(function (ValidateType) {
    ValidateType["DEPLOY"] = "DEPLOY";
    ValidateType["CALL"] = "CALL";
    ValidateType["INVOKE"] = "INVOKE";
})(ValidateType || (ValidateType = {}));
export var Uint;
(function (Uint) {
    Uint["u8"] = "core::integer::u8";
    Uint["u16"] = "core::integer::u16";
    Uint["u32"] = "core::integer::u32";
    Uint["u64"] = "core::integer::u64";
    Uint["u128"] = "core::integer::u128";
    Uint["u256"] = "core::integer::u256";
    Uint["u512"] = "core::integer::u512";
})(Uint || (Uint = {}));
export var Literal;
(function (Literal) {
    Literal["ClassHash"] = "core::starknet::class_hash::ClassHash";
    Literal["ContractAddress"] = "core::starknet::contract_address::ContractAddress";
    Literal["Secp256k1Point"] = "core::starknet::secp256k1::Secp256k1Point";
})(Literal || (Literal = {}));

```

## High-Level Overview

This is a JavaScript file located at `js/src/static_dependencies/starknet/types/calldata.js`.



## Detailed Walkthrough

### Code Structure

- Total lines: 23
- Code lines: 22
- Comment lines: 0
- Blank lines: 1

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this JavaScript file:**

```bash
node js/src/static_dependencies/starknet/types/calldata.js
```

