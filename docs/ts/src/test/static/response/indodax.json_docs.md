# Documentation: ts/src/test/static/response/indodax.json

## File Metadata

- **Path**: `ts/src/test/static/response/indodax.json`
- **Size**: 2,145 bytes
- **Lines**: 61
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "exchange": "indodax",
    "skipKeys": [],
    "methods": {
        "fetchTrades": [],
        "fetchTicker": [
            {
                "description": "public spot ticker",
                "method": "fetchTicker",
                "input": [
                    "BTC/USDT"
                ],
                "httpResponse": {
                    "ticker": {
                        "high": "73595.39",
                        "low": "69500",
                        "vol_btc": "1.58603722",
                        "vol_usdt": "113619.71423736",
                        "last": "73302",
                        "buy": "73302",
                        "sell": "73594.990001",
                        "server_time": "1710328244"
                    }
                },
                "parsedResponse": {
                    "symbol": "BTC/USDT",
                    "timestamp": 1710328244000,
                    "datetime": "2024-03-13T11:10:44.000Z",
                    "high": 73595.39,
                    "low": 69500,
                    "bid": 73302,
                    "bidVolume": null,
                    "ask": 73594.990001,
                    "askVolume": null,
                    "vwap": 71637.48290683872,
                    "open": null,
                    "close": 73302,
                    "last": 73302,
                    "previousClose": null,
                    "change": null,
                    "percentage": null,
                    "average": null,
                    "baseVolume": 1.58603722,
                    "quoteVolume": 113619.71423736,
                    "markPrice": null,
                    "indexPrice": null,
                    "info": {
                        "high": "73595.39",
                        "low": "69500",
                        "vol_btc": "1.58603722",
                        "vol_usdt": "113619.71423736",
                        "last": "73302",
                        "buy": "73302",
                        "sell": "73594.990001",
                        "server_time": "1710328244"
                    }
                }
            }
        ]
    }
}
```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/response/indodax.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 61
- Code lines: 61
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
