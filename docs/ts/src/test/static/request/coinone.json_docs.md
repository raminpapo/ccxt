# Documentation: ts/src/test/static/request/coinone.json

## File Metadata

- **Path**: `ts/src/test/static/request/coinone.json`
- **Size**: 2,401 bytes
- **Lines**: 80
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "exchange": "bitbns",
    "skipKeys": [],
    "outputType": "json",
    "methods": {
        "fetchCurrencies": [
            {
                "description": "fetchCurrencies",
                "method": "fetchCurrencies",
                "url": "https://api.coinone.co.kr/public/v2/currencies",
                "input": [],
                "output": null
            },
            {
                "description": "fetchCurrencies",
                "method": "fetchCurrencies",
                "url": "https://api.coinone.co.kr/public/v2/currencies",
                "input": []
            }
        ],
        "fetchMarkets": [
            {
                "description": "fetchMarkets",
                "method": "fetchMarkets",
                "url": "https://api.coinone.co.kr/public/v2/ticker_new/KRW",
                "input": []
            }
        ],
        "fetchOrderBook": [
            {
                "description": "fetchOrderBook",
                "method": "fetchOrderBook",
                "url": "https://api.coinone.co.kr/public/v2/orderbook/KRW/BTC",
                "input": [
                    "BTC/KRW"
                ]
            }
        ],
        "fetchTickers": [
            {
                "description": "fetchTickers",
                "method": "fetchTickers",
                "url": "https://api.coinone.co.kr/public/v2/ticker_new/KRW",
                "input": [
                ]
            },
            {
                "description": "fetchTickers",
                "method": "fetchTickers",
                "url": "https://api.coinone.co.kr/public/v2/ticker_new/KRW/BTC",
                "input": [
                    [
                        "BTC/KRW"
                    ]
                ]
            }
        ],
        "fetchTicker": [
            {
                "description": "fetchTicker",
                "method": "fetchTicker",
                "url": "https://api.coinone.co.kr/public/v2/ticker_new/KRW/BTC",
                "input": [
                    "BTC/KRW"
                ]
            }
        ],
        "fetchTrades": [
            {
                "description": "fetchTrades",
                "method": "fetchTrades",
                "url": "https://api.coinone.co.kr/public/v2/trades/KRW/BTC",
                "input": [
                    "BTC/KRW"
                ]
            }
        ]
    }
}

```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/request/coinone.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 80
- Code lines: 79
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
