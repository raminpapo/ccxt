# Documentation: ts/src/test/static/request/bitflyer.json

## File Metadata

- **Path**: `ts/src/test/static/request/bitflyer.json`
- **Size**: 443 bytes
- **Lines**: 19
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "exchange": "bitflyer",
    "skipKeys": [
    ],
    "outputType": "json",
    "methods": {
        "fetchFundingRate": [
            {
                "description": "Fetch Funding Rate",
                "method": "fetchFundingRate",
                "url": "https://api.bitflyer.com/v1/getfundingrate?product_code=FX_BTC_JPY",
                "input": [
                  "BTC/JPY:JPY"
                ]
            }
        ]
    }
}

```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/request/bitflyer.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 19
- Code lines: 18
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
