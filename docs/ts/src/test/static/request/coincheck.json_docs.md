# Documentation: ts/src/test/static/request/coincheck.json

## File Metadata

- **Path**: `ts/src/test/static/request/coincheck.json`
- **Size**: 571 bytes
- **Lines**: 22
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "exchange": "coincheck",
    "outputType": "both",
    "methods": {
        "createOrder": [
            {
                "description": "Spot limit buy order",
                "method": "createOrder",
                "url": "https://api.coincatch.com/api/exchange/orders",
                "input": [
                  "BTC/JPY",
                  "limit",
                  "buy",
                  0.0001,
                  25000
                ],
                "output": "amount=0.0001&order_type=buy&pair=btc_jpy&rate=25000"
            }
        ]
    }
}

```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/request/coincheck.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 22
- Code lines: 21
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

This appears to be a test file.

**To run this test:**
