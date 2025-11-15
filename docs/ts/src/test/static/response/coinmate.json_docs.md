# Documentation: ts/src/test/static/response/coinmate.json

## File Metadata

- **Path**: `ts/src/test/static/response/coinmate.json`
- **Size**: 2,711 bytes
- **Lines**: 81
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "exchange": "coinmate",
    "skipKeys": [],
    "methods": {
        "fetchTrades": [
            {
                "description": "public spot trades",
                "method": "fetchTrades",
                "input": [
                    "BTC/USDT",
                    null,
                    1
                ],
                "httpResponse": {
                    "error": false,
                    "errorMessage": null,
                    "data": []
                },
                "parsedResponse": []
            }
        ],
        "fetchTicker": [
            {
                "description": "public spot ticker",
                "method": "fetchTicker",
                "input": [
                    "BTC/USDT"
                ],
                "httpResponse": {
                    "error": false,
                    "errorMessage": null,
                    "data": {
                        "last": "73722.8",
                        "high": "73726.3",
                        "low": "69000",
                        "amount": "0.15487888",
                        "bid": "73017.7",
                        "ask": "73667.9",
                        "change": "3.05116019",
                        "open": "71540",
                        "timestamp": "1710328244"
                    }
                },
                "parsedResponse": {
                    "symbol": "BTC/USDT",
                    "timestamp": 1710328244000,
                    "datetime": "2024-03-13T11:10:44.000Z",
                    "high": 73726.3,
                    "low": 69000,
                    "bid": 73017.7,
                    "bidVolume": null,
                    "ask": 73667.9,
                    "vwap": null,
                    "askVolume": null,
                    "open": null,
                    "close": 73722.8,
                    "last": 73722.8,
                    "previousClose": null,
                    "change": null,
                    "percentage": null,
                    "average": null,
                    "baseVolume": 0.15487888,
                    "quoteVolume": null,
                    "markPrice":  null,
                    "indexPrice": null,
                    "info": {
                        "last": "73722.8",
                        "high": "73726.3",
                        "low": "69000",
                        "amount": "0.15487888",
                        "bid": "73017.7",
                        "ask": "73667.9",
                        "change": "3.05116019",
                        "open": "71540",
                        "timestamp": "1710328244"
                    }
                }
            }
        ]
    }
}
```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/response/coinmate.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 81
- Code lines: 81
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
