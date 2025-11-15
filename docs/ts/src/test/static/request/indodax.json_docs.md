# Documentation: ts/src/test/static/request/indodax.json

## File Metadata

- **Path**: `ts/src/test/static/request/indodax.json`
- **Size**: 929 bytes
- **Lines**: 34
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "exchange": "indodax",
    "skipKeys": [
        "timestamp",
        "from",
        "to"
    ],
    "outputType": "both",
    "methods": {
        "fetchDepositAddresses": [
            {
                "description": "Fetch Deposit Addresses",
                "method": "fetchDepositAddresses",
                "url": "https://indodax.com/tapi",
                "input": [],
                "output": "method=getInfo&timestamp=1708039102346&recvWindow=5000"
            }
        ],
        "fetchOHLCV": [
            {
                "description": "fetchOHLCV",
                "method": "fetchOHLCV",
                "url": "https://indodax.com/tradingview/history_v2?to=1708417630&tf=60&symbol=btc_usdt&from=1708399629",
                "input": [
                    "BTC/USDT",
                    "1h",
                    1708399629000,
                    5
                ]
            }
        ]
    }
}

```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/request/indodax.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 34
- Code lines: 33
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
