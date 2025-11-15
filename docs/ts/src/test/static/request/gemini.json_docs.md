# Documentation: ts/src/test/static/request/gemini.json

## File Metadata

- **Path**: `ts/src/test/static/request/gemini.json`
- **Size**: 2,719 bytes
- **Lines**: 92
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "exchange": "gemini",
    "skipKeys": [],
    "outputType": "json",
    "methods": {
        "fetchTrades": [
            {
                "description": "spot fetchTrades",
                "method": "fetchTrades",
                "url": "https://api.gemini.com/v1/trades/btcusdt",
                "input": [
                    "BTC/USDT"
                ]
            }
        ],
        "fetchOrderBook": [
            {
                "description": "spot orderbook",
                "method": "fetchOrderBook",
                "url": "https://api.gemini.com/v1/book/btcusdt",
                "input": [
                    "BTC/USDT"
                ]
            }
        ],
        "fetchTicker": [
            {
                "description": "spot ticker",
                "method": "fetchTicker",
                "url": "https://api.gemini.com/v1/pubticker/btcusdt",
                "input": [
                    "BTC/USDT"
                ]
            },
            {
                "description": "usdcusdc ticker",
                "method": "fetchTicker",
                "url": "https://api.gemini.com/v1/pubticker/usdcusd",
                "input": [
                  "USDC/USD"
                ]
            },
            {
                "description": "sol btc ticker",
                "method": "fetchTicker",
                "url": "https://api.gemini.com/v1/pubticker/solbtc",
                "input": [
                  "SOL/BTC"
                ]
            },
            {
                "description": "swap ticker",
                "method": "fetchTicker",
                "url": "https://api.gemini.com/v1/pubticker/btcgusdperp",
                "input": [
                  "BTC/GUSD:GUSD"
                ]
            },
            {
                "description": "paxg ticker",
                "method": "fetchTicker",
                "url": "https://api.gemini.com/v1/pubticker/paxgusd",
                "input": [
                  "PAXG/USD"
                ]
            }
        ],
        "fetchTickers": [
            {
                "description": "spot tickers",
                "method": "fetchTickers",
                "url": "https://api.gemini.com/v1/pricefeed",
                "input": [
                    [
                        "BTC/USDT",
                        "ETH/USDT"
                    ]
                ]
            }
        ],
        "fetchOHLCV": [
            {
                "description": "spot ohlcv",
                "method": "fetchOHLCV",
                "url": "https://api.gemini.com/v2/candles/btcusdt/1m",
                "input": [
                    "BTC/USDT"
                ]
            }
        ]
    }
}
```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/request/gemini.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 92
- Code lines: 92
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
