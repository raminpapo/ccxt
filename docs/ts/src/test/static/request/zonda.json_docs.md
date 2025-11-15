# Documentation: ts/src/test/static/request/zonda.json

## File Metadata

- **Path**: `ts/src/test/static/request/zonda.json`
- **Size**: 3,977 bytes
- **Lines**: 122
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "exchange": "zonda",
    "skipKeys": ["from", "to"],
    "outputType": "json",
    "methods": {
        "fetchMyTrades": [
            {
                "description": "Spot private trades",
                "method": "fetchMyTrades",
                "url": "https://api.zondacrypto.exchange/rest/trading/history/transactions?query=%7B%22markets%22%3A%5B%22LTC-USDT%22%5D%7D",
                "input": [
                    "LTC/USDT",
                    1699457638000,
                    5
                ]
            }
        ],
        "fetchOpenOrders": [
            {
                "description": "Spot open orders",
                "method": "fetchOpenOrders",
                "url": "https://api.zondacrypto.exchange/rest/trading/offer",
                "input": [
                    "LTC/USDT"
                ]
            },
            {
                "description": "Swap open orders",
                "method": "fetchOpenOrders",
                "url": "https://api.zondacrypto.exchange/rest/trading/offer",
                "input": [
                    "LTC/USDT:USDT"
                ]
            }
        ],
        "fetchBalance": [
            {
                "description": "Fetch spot Balance",
                "method": "fetchBalance",
                "url": "https://api.zondacrypto.exchange/rest/balances/BITBAY/balance?type=spot",
                "input": [
                    {
                        "type": "spot"
                    }
                ]
            },
            {
                "description": "Fetch swap Balance",
                "method": "fetchBalance",
                "url": "https://api.zondacrypto.exchange/rest/balances/BITBAY/balance?type=swap",
                "input": [
                    {
                        "type": "swap"
                    }
                ]
            }
        ],
        "fetchLedger": [
            {
                "description": "fetch USDT ledger",
                "method": "fetchLedger",
                "url": "https://api.zondacrypto.exchange/rest/balances/BITBAY/history?query=%7B%22balanceCurrencies%22%3A%5B%22USDT%22%5D%7D",
                "input": [
                    "USDT"
                ]
            }
        ],
        "fetchTrades": [
            {
                "description": "spot fetchTrades",
                "method": "fetchTrades",
                "url": "https://api.zondacrypto.exchange/rest/trading/transactions/BTC-USDT",
                "input": [
                    "BTC/USDT"
                ]
            }
        ],
        "fetchOrderBook": [
            {
                "description": "spot orderbook",
                "method": "fetchOrderBook",
                "url": "https://api.zondacrypto.exchange/rest/trading/orderbook/BTC-USDT",
                "input": [
                    "BTC/USDT"
                ]
            }
        ],
        "fetchTicker": [
            {
                "description": "spot ticker",
                "method": "fetchTicker",
                "url": "https://api.zondacrypto.exchange/rest/trading/ticker/BTC-USDT",
                "input": [
                    "BTC/USDT"
                ]
            }
        ],
        "fetchTickers": [
            {
                "description": "spot tickers",
                "method": "fetchTickers",
                "url": "https://api.zondacrypto.exchange/rest/trading/ticker",
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
                "url": "https://api.zondacrypto.exchange/rest/trading/candle/history/BTC-USDT/60?to=1709992984698&from=1709986984698",
                "input": [
                    "BTC/USDT"
                ]
            }
        ]
    }
}
```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/request/zonda.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 122
- Code lines: 122
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
