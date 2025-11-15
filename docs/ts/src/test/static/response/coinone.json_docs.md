# Documentation: ts/src/test/static/response/coinone.json

## File Metadata

- **Path**: `ts/src/test/static/response/coinone.json`
- **Size**: 2,556 bytes
- **Lines**: 68
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "exchange": "coinone",
    "skipKeys": [],
    "methods": {
        "fetchCurrencies": [
            {
                "description": "fetchCurrencies",
                "method": "fetchCurrencies",
                "input": [],
                "httpResponse": {
                    "result": "success",
                    "error_code": "0",
                    "server_time": "1747504992748",
                    "currencies": [
                        {
                            "name": "Tether USDT",
                            "symbol": "USDT",
                            "deposit_status": "normal",
                            "withdraw_status": "normal",
                            "deposit_confirm_count": "20",
                            "max_precision": "6",
                            "deposit_fee": "0.0",
                            "withdrawal_min_amount": "1.0",
                            "withdrawal_fee": "2.0"
                        }
                    ]
                },
                "parsedResponse": {
                    "USDT": {
                        "info": {
                            "name": "Tether USDT",
                            "symbol": "USDT",
                            "deposit_status": "normal",
                            "withdraw_status": "normal",
                            "deposit_confirm_count": "20",
                            "max_precision": "6",
                            "deposit_fee": "0.0",
                            "withdrawal_min_amount": "1.0",
                            "withdrawal_fee": "2.0"
                        },
                        "id": "USDT",
                        "numericId": null,
                        "code": "USDT",
                        "precision": 0.000001,
                        "type": "crypto",
                        "name": "Tether USDT",
                        "active": null,
                        "deposit": true,
                        "withdraw": true,
                        "fee": 2,
                        "fees": {},
                        "networks": {},
                        "limits": {
                            "amount": {
                                "min": null,
                                "max": null
                            },
                            "withdraw": {
                                "min": 1,
                                "max": null
                            }
                        }
                    }
                }
            }
        ]
  }
}
```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/response/coinone.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 68
- Code lines: 68
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
