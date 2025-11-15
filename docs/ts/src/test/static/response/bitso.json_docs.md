# Documentation: ts/src/test/static/response/bitso.json

## File Metadata

- **Path**: `ts/src/test/static/response/bitso.json`
- **Size**: 4,430 bytes
- **Lines**: 120
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "exchange": "bitso",
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
                    "success": true,
                    "payload": [
                        {
                            "book": "btc_usdt",
                            "created_at": "2024-03-13T10:59:59+0000",
                            "amount": "0.00007045",
                            "maker_side": "sell",
                            "price": "73320",
                            "tid": "119089863"
                        }
                    ]
                },
                "parsedResponse": [
                    {
                        "id": "119089863",
                        "info": {
                            "book": "btc_usdt",
                            "created_at": "2024-03-13T10:59:59+0000",
                            "amount": "0.00007045",
                            "maker_side": "sell",
                            "price": "73320",
                            "tid": "119089863"
                        },
                        "timestamp": 1710327599000,
                        "datetime": "2024-03-13T10:59:59.000Z",
                        "symbol": "BTC/USDT",
                        "order": null,
                        "type": null,
                        "side": "buy",
                        "takerOrMaker": null,
                        "price": 73320,
                        "amount": 0.00007045,
                        "cost": 5.165394,
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
                    "success": true,
                    "payload": {
                        "high": "73681",
                        "last": "73440",
                        "created_at": "2024-03-13T11:10:45+00:00",
                        "book": "btc_usdt",
                        "volume": "33.96216034",
                        "vwap": "71004.0822715099",
                        "low": "68696",
                        "ask": "73440",
                        "bid": "73288",
                        "change_24": "1239",
                        "rolling_average_change": {
                            "6": "0.2759"
                        }
                    }
                },
                "parsedResponse": {
                    "symbol": "BTC/USDT",
                    "timestamp": 1710328245000,
                    "datetime": "2024-03-13T11:10:45.000Z",
                    "high": 73681,
                    "low": 68696,
                    "bid": 73288,
                    "bidVolume": null,
                    "ask": 73440,
                    "askVolume": null,
                    "vwap": 71004.0822715099,
                    "open": null,
                    "close": 73440,
                    "last": 73440,
                    "previousClose": null,
                    "change": null,
                    "percentage": null,
                    "average": null,
                    "baseVolume": 33.96216034,
                    "quoteVolume": 2411452.0268995706,
                    "markPrice":  null,
                    "indexPrice": null,
                    "info": {
                        "high": "73681",
                        "last": "73440",
                        "created_at": "2024-03-13T11:10:45+00:00",
                        "book": "btc_usdt",
                        "volume": "33.96216034",
                        "vwap": "71004.0822715099",
                        "low": "68696",
                        "ask": "73440",
                        "bid": "73288",
                        "change_24": "1239",
                        "rolling_average_change": {
                            "6": "0.2759"
                        }
                    }
                }
            }
        ]
    }
}
```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/response/bitso.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 120
- Code lines: 120
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
