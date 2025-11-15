# Documentation: ts/src/test/static/currencies/bitopro.json

## File Metadata

- **Path**: `ts/src/test/static/currencies/bitopro.json`
- **Size**: 3,087 bytes
- **Lines**: 127
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "BTC": {
        "id": "BTC",
        "code": "BTC",
        "info": {
            "currency": "BTC",
            "withdrawFee": "0.0001",
            "minWithdraw": "0.0005",
            "maxWithdraw": "50",
            "maxDailyWithdraw": "100",
            "withdraw": true,
            "deposit": true,
            "depositConfirmation": "3"
        },
        "active": true,
        "deposit": true,
        "withdraw": true,
        "fee": 0.0001,
        "limits": {
            "withdraw": {
                "min": 0.0005,
                "max": 50
            },
            "amount": {}
        }
    },
    "LTC": {
        "id": "LTC",
        "code": "LTC",
        "info": {
            "currency": "LTC",
            "withdrawFee": "0.001",
            "minWithdraw": "0.002",
            "maxWithdraw": "2000",
            "maxDailyWithdraw": "5000",
            "withdraw": true,
            "deposit": true,
            "depositConfirmation": "5"
        },
        "active": true,
        "deposit": true,
        "withdraw": true,
        "fee": 0.001,
        "limits": {
            "withdraw": {
                "min": 0.002,
                "max": 2000
            },
            "amount": {}
        }
    },
    "ETH": {
        "id": "ETH",
        "code": "ETH",
        "info": {
            "currency": "ETH",
            "withdrawFee": "0.0025",
            "minWithdraw": "0.001",
            "maxWithdraw": "500",
            "maxDailyWithdraw": "1000",
            "withdraw": true,
            "deposit": true,
            "depositConfirmation": "64"
        },
        "active": true,
        "deposit": true,
        "withdraw": true,
        "fee": 0.0025,
        "limits": {
            "withdraw": {
                "min": 0.001,
                "max": 500
            },
            "amount": {}
        }
    },
    "ADA": {
        "id": "ADA",
        "code": "ADA",
        "info": {
            "currency": "ADA",
            "withdrawFee": "1",
            "minWithdraw": "3",
            "maxWithdraw": "50000",
            "maxDailyWithdraw": "200000",
            "withdraw": true,
            "deposit": true,
            "depositConfirmation": "35"
        },
        "active": true,
        "deposit": true,
        "withdraw": true,
        "fee": 1,
        "limits": {
            "withdraw": {
                "min": 3,
                "max": 50000
            },
            "amount": {}
        }
    },
    "XRP": {
        "id": "XRP",
        "code": "XRP",
        "info": {
            "currency": "XRP",
            "withdrawFee": "0.25",
            "minWithdraw": "25",
            "maxWithdraw": "50000",
            "maxDailyWithdraw": "100000",
            "withdraw": true,
            "deposit": true,
            "depositConfirmation": "6"
        },
        "active": true,
        "deposit": true,
        "withdraw": true,
        "fee": 0.25,
        "limits": {
            "withdraw": {
                "min": 25,
                "max": 50000
            },
            "amount": {}
        }
    }
}
```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/currencies/bitopro.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 127
- Code lines: 127
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
