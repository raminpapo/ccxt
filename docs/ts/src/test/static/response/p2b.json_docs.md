# Documentation: ts/src/test/static/response/p2b.json

## File Metadata

- **Path**: `ts/src/test/static/response/p2b.json`
- **Size**: 3,722 bytes
- **Lines**: 108
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "exchange": "p2b",
    "skipKeys": [],
    "methods": {
        "fetchTicker": [
            {
                "description": "public spot ticker",
                "method": "fetchTicker",
                "input": [
                    "BTC/USDT"
                ],
                "httpResponse": {
                    "success": true,
                    "errorCode": "",
                    "message": "",
                    "result": {
                        "bid": "73373.34",
                        "ask": "73373.78",
                        "open": "72176.06",
                        "high": "73640.82",
                        "low": "68692.97",
                        "last": "73373.56",
                        "volume": "12812.820809",
                        "deal": "919528790.98908515",
                        "change": "1.65"
                    },
                    "cache_time": "1710328222.314526",
                    "current_time": "1710328226.582696"
                },
                "parsedResponse": {
                    "timestamp": null,
                    "datetime": null,
                    "symbol": "BTC/USDT",
                    "high": 73640.82,
                    "low": 68692.97,
                    "bid": 73373.34,
                    "bidVolume": null,
                    "ask": 73373.78,
                    "askVolume": null,
                    "vwap": 71766.30382149639,
                    "open": 72176.06,
                    "close": 73373.56,
                    "last": 73373.56,
                    "previousClose": null,
                    "change": 1197.5,
                    "percentage": 1.65,
                    "average": 72774.81,
                    "baseVolume": 12812.820809,
                    "quoteVolume": 919528790.9890852,
                    "markPrice": null,
                    "indexPrice": null,
                    "info": {
                        "bid": "73373.34",
                        "ask": "73373.78",
                        "open": "72176.06",
                        "high": "73640.82",
                        "low": "68692.97",
                        "last": "73373.56",
                        "volume": "12812.820809",
                        "deal": "919528790.98908515",
                        "change": "1.65"
                    }
                }
            }
        ],
        "fetchOHLCV": [
            {
                "description": "public spot ohlcv",
                "method": "fetchOHLCV",
                "input": [
                    "BTC/USDT",
                    "1h",
                    null,
                    1
                ],
                "httpResponse": {
                    "success": true,
                    "errorCode": "",
                    "message": "",
                    "result": [
                        [
                            1710327600,
                            "73258.78",
                            "73426.86",
                            "73442.95",
                            "73238.54",
                            "86.366247",
                            "6333531.64405854",
                            "BTC_USDT"
                        ]
                    ],
                    "cache_time": "1710328420.989743",
                    "current_time": "1710328420.989905"
                },
                "parsedResponse": [
                    [
                        1710327600000,
                        73258.78,
                        73442.95,
                        73238.54,
                        73426.86,
                        86.366247
                    ]
                ]
            }
        ]
    }
}
```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/response/p2b.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 108
- Code lines: 108
- Comment lines: 0
- Blank lines: 0

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Implements caching mechanisms



## Related Files

No explicit file references found.



## Testing & Execution

This appears to be a test file.

**To run this test:**
