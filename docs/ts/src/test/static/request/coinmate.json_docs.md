# Documentation: ts/src/test/static/request/coinmate.json

## File Metadata

- **Path**: `ts/src/test/static/request/coinmate.json`
- **Size**: 646 bytes
- **Lines**: 26
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "exchange": "coinmate",
    "skipKeys": [],
    "outputType": "json",
    "methods": {
        "fetchTicker": [
            {
                "description": "fetchTicker",
                "method": "fetchTicker",
                "url": "https://coinmate.io/api/ticker?currencyPair=BTC_EUR",
                "input": [
                    "BTC/EUR"
                ]
            }
        ],
        "fetchTickers": [
            {
                "description": "fetchTickers",
                "method": "fetchTickers",
                "url": "https://coinmate.io/api/tickerAll",
                "input": []
            }
        ]
    }
}

```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/request/coinmate.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 26
- Code lines: 25
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
