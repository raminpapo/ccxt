# Documentation: ts/src/test/static/request/p2b.json

## File Metadata

- **Path**: `ts/src/test/static/request/p2b.json`
- **Size**: 3,954 bytes
- **Lines**: 114
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "exchange": "p2b",
    "skipKeys": [
        "nonce",
        "startTime",
        "endTime"
    ],
    "outputType": "json",
    "methods": {
        "createOrder": [
            {
                "description": "Spot limit buy",
                "method": "createOrder",
                "url": "https://api.p2pb2b.com/api/v2/order/new",
                "input": [
                    "LTC/USDT",
                    "limit",
                    "buy",
                    0.1,
                    55
                ],
                "output": "{\"market\":\"LTC_USDT\",\"side\":\"buy\",\"amount\":\"0.1\",\"price\":\"55\",\"request\":\"/api/v2/order/new\",\"nonce\":\"1700046291\"}"
            },
            {
                "description": "Limit sell order",
                "method": "createOrder",
                "url": "https://api.p2pb2b.com/api/v2/order/new",
                "input": [
                    "LTC/USDT",
                    "limit",
                    "sell",
                    0.1,
                    100
                ],
                "output": "{\"market\":\"LTC_USDT\",\"side\":\"sell\",\"amount\":\"0.1\",\"price\":\"100\",\"request\":\"/api/v2/order/new\",\"nonce\":\"1700046477\"}"
            }
        ],
        "cancelOrder": [
            {
                "description": "Cancel spot order",
                "method": "cancelOrder",
                "url": "https://api.p2pb2b.com/api/v2/order/cancel",
                "input": [
                    "175340201831",
                    "LTC/USDT"
                ],
                "output": "{\"market\":\"LTC_USDT\",\"orderId\":\"175340201831\",\"request\":\"/api/v2/order/cancel\",\"nonce\":\"1700046336\"}"
            }
        ],
        "fetchMyTrades": [
            {
                "description": "Fetch spot trades",
                "method": "fetchMyTrades",
                "url": "https://api.p2pb2b.com/api/v2/account/market_deal_history",
                "input": [
                    "LTC/USDT"
                ],
                "output": "{\"market\":\"LTC_USDT\",\"startTime\":1699960007,\"endTime\":1700046407,\"request\":\"/api/v2/account/market_deal_history\",\"nonce\":\"1700046407\"}"
            }
        ],
        "fetchBalance": [
            {
                "description": "Fetch balance",
                "method": "fetchBalance",
                "url": "https://api.p2pb2b.com/api/v2/account/balances",
                "input": [],
                "output": "{\"request\":\"/api/v2/account/balances\",\"nonce\":\"1700046634\"}"
            }
        ],
        "fetchOrderBook": [
            {
                "description": "spot orderbook",
                "method": "fetchOrderBook",
                "url": "https://api.p2pb2b.com/api/v2/public/depth/result?market=BTC_USDT",
                "input": [
                    "BTC/USDT"
                ]
            }
        ],
        "fetchTicker": [
            {
                "description": "spot ticker",
                "method": "fetchTicker",
                "url": "https://api.p2pb2b.com/api/v2/public/ticker?market=BTC_USDT",
                "input": [
                    "BTC/USDT"
                ]
            }
        ],
        "fetchTickers": [
            {
                "description": "spot tickers",
                "method": "fetchTickers",
                "url": "https://api.p2pb2b.com/api/v2/public/tickers",
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
                "url": "https://api.p2pb2b.com/api/v2/public/market/kline?market=BTC_USDT&interval=1m",
                "input": [
                    "BTC/USDT"
                ]
            }
        ]
    }
}
```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/request/p2b.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 114
- Code lines: 114
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
