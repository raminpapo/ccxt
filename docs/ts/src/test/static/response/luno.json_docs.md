# Documentation: ts/src/test/static/response/luno.json

## File Metadata

- **Path**: `ts/src/test/static/response/luno.json`
- **Size**: 3,692 bytes
- **Lines**: 102
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "exchange": "luno",
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
                    "trades": [
                        {
                            "sequence": "26963",
                            "timestamp": "1710325156438",
                            "price": "73998.98000000",
                            "volume": "0.00080000",
                            "is_buy": true
                        }
                    ]
                },
                "parsedResponse": [
                    {
                        "info": {
                            "sequence": "26963",
                            "timestamp": "1710325156438",
                            "price": "73998.98000000",
                            "volume": "0.00080000",
                            "is_buy": true
                        },
                        "id": "26963",
                        "timestamp": 1710325156438,
                        "datetime": "2024-03-13T10:19:16.438Z",
                        "symbol": "BTC/USDT",
                        "order": null,
                        "type": null,
                        "side": "buy",
                        "takerOrMaker": null,
                        "price": 73998.98,
                        "amount": 0.0008,
                        "cost": 59.199184,
                        "fee": {"cost": null, "currency": null },
                        "fees": []
                    }
                ]
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
                    "pair": "XBTUSDT",
                    "timestamp": "1710328244969",
                    "bid": "72617.38000000",
                    "ask": "73998.97000000",
                    "last_trade": "73998.98000000",
                    "rolling_24_hour_volume": "0.31110000",
                    "status": "ACTIVE"
                },
                "parsedResponse": {
                    "symbol": "BTC/USDT",
                    "timestamp": 1710328244969,
                    "datetime": "2024-03-13T11:10:44.969Z",
                    "high": null,
                    "low": null,
                    "bid": 72617.38,
                    "bidVolume": null,
                    "ask": 73998.97,
                    "askVolume": null,
                    "vwap": null,
                    "open": null,
                    "close": 73998.98,
                    "last": 73998.98,
                    "previousClose": null,
                    "change": null,
                    "percentage": null,
                    "average": null,
                    "baseVolume": 0.3111,
                    "quoteVolume": null,
                    "markPrice":  null,
                    "indexPrice": null,
                    "info": {
                        "pair": "XBTUSDT",
                        "timestamp": "1710328244969",
                        "bid": "72617.38000000",
                        "ask": "73998.97000000",
                        "last_trade": "73998.98000000",
                        "rolling_24_hour_volume": "0.31110000",
                        "status": "ACTIVE"
                    }
                }
            }
        ]
    }
}
```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/response/luno.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 102
- Code lines: 102
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
