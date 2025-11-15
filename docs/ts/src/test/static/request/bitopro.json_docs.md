# Documentation: ts/src/test/static/request/bitopro.json

## File Metadata

- **Path**: `ts/src/test/static/request/bitopro.json`
- **Size**: 2,057 bytes
- **Lines**: 71
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "exchange": "bitopro",
    "skipKeys": ["from", "to"],
    "outputType": "json",
    "methods": {
        "fetchTrades": [
            {
                "description": "spot fetchTrades",
                "method": "fetchTrades",
                "url": "https://api.bitopro.com/v3/trades/btc_usdt",
                "input": [
                    "BTC/USDT"
                ]
            }
        ],
        "fetchOrderBook": [
            {
                "description": "spot orderbook",
                "method": "fetchOrderBook",
                "url": "https://api.bitopro.com/v3/order-book/btc_usdt",
                "input": [
                    "BTC/USDT"
                ]
            }
        ],
        "fetchTicker": [
            {
                "description": "spot ticker",
                "method": "fetchTicker",
                "url": "https://api.bitopro.com/v3/tickers/btc_usdt",
                "input": [
                    "BTC/USDT"
                ]
            }
        ],
        "fetchTickers": [
            {
                "description": "spot tickers",
                "method": "fetchTickers",
                "url": "https://api.bitopro.com/v3/tickers",
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
                "url": "https://api.bitopro.com/v3/trading-history/btc_usdt?resolution=1m&to=1709992985&from=1709962985",
                "input": [
                    "BTC/USDT"
                ]
            }
        ],
        "fetchOpenOrders": [
            {
                "description": "fetchOpenOrders",
                "method": "fetchOpenOrders",
                "url": "https://api.bitopro.com/v3/orders/open?pair=btc_usdt",
                "input": [
                    "BTC/USDT"
                ]
            }
        ]
    }
}

```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/request/bitopro.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 71
- Code lines: 70
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
