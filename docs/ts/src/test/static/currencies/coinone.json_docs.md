# Documentation: ts/src/test/static/currencies/coinone.json

## File Metadata

- **Path**: `ts/src/test/static/currencies/coinone.json`
- **Size**: 1,793 bytes
- **Lines**: 72
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "BTC": {
        "info": {
            "name": "Bitcoin",
            "symbol": "BTC",
            "deposit_status": "normal",
            "withdraw_status": "normal",
            "deposit_confirm_count": "2",
            "max_precision": "8",
            "deposit_fee": "0.0",
            "withdrawal_min_amount": "0.0001",
            "withdrawal_fee": "0.0008"
        },
        "id": "BTC",
        "numericId": null,
        "code": "BTC",
        "precision": 1e-8,
        "type": "crypto",
        "name": "Bitcoin",
        "active": null,
        "deposit": true,
        "withdraw": true,
        "fee": 0.0008,
        "fees": {},
        "networks": {},
        "limits": {
            "amount": {
                "min": null,
                "max": null
            },
            "withdraw": {
                "min": 0.0001,
                "max": null
            }
        }
    },
    "KRW": {
        "info": {
            "name": "Won",
            "symbol": "KRW",
            "deposit_status": "normal",
            "withdraw_status": "normal",
            "deposit_confirm_count": "0",
            "max_precision": "0",
            "deposit_fee": "0.0",
            "withdrawal_min_amount": "5000.0",
            "withdrawal_fee": "1000.0"
        },
        "id": "KRW",
        "numericId": null,
        "code": "KRW",
        "precision": 1,
        "type": "fiat",
        "name": "Won",
        "active": null,
        "deposit": true,
        "withdraw": true,
        "fee": 1000,
        "fees": {},
        "networks": {},
        "limits": {
            "amount": {
                "min": null,
                "max": null
            },
            "withdraw": {
                "min": 5000,
                "max": null
            }
        }
    }
}
```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/currencies/coinone.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 72
- Code lines: 72
- Comment lines: 0
- Blank lines: 0

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

This appears to be a test file.

**To run this test:**
