# Documentation: ts/src/test/static/request/btcalpha.json

## File Metadata

- **Path**: `ts/src/test/static/request/btcalpha.json`
- **Size**: 4,741 bytes
- **Lines**: 155
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "exchange": "btcalpha",
    "skipKeys": [],
    "outputType": "urlencoded",
    "methods": {
        "fetchOrders": [
            {
                "description": "Spot orders",
                "method": "fetchOrders",
                "url": "https://btc-alpha.com/api/v1/orders/own/?pair=LTC_USDT",
                "input": [
                    "LTC/USDT"
                ]
            }
        ],
        "fetchMyTrades": [
            {
                "description": "Spot private trades",
                "method": "fetchMyTrades",
                "url": "https://btc-alpha.com/api/v1/exchanges/own/?limit=5&pair=LTC_USDT",
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
                "url": "https://btc-alpha.com/api/v1/orders/own/?pair=LTC_USDT&status=1",
                "input": [
                    "LTC/USDT"
                ]
            }
        ],
        "fetchClosedOrders": [
            {
                "description": "Spot closed orders",
                "method": "fetchClosedOrders",
                "url": "https://btc-alpha.com/api/v1/orders/own/?pair=LTC_USDT&status=3",
                "input": [
                    "LTC/USDT"
                ]
            }
        ],
        "fetchBalance": [
            {
                "description": "Fetch spot Balance",
                "method": "fetchBalance",
                "url": "https://btc-alpha.com/api/v1/wallets/?type=spot",
                "input": [
                    {
                        "type": "spot"
                    }
                ]
            },
            {
                "description": "Fetch swap Balance",
                "method": "fetchBalance",
                "url": "https://btc-alpha.com/api/v1/wallets/?type=swap",
                "input": [
                    {
                        "type": "swap"
                    }
                ]
            }
        ],
        "fetchDeposits": [
            {
                "description": "Fetch deposits",
                "method": "fetchDeposits",
                "url": "https://btc-alpha.com/api/v1/deposits/",
                "input": []
            }
        ],
        "fetchWithdrawals": [
            {
                "description": "Fetch withdrawals",
                "method": "fetchWithdrawals",
                "url": "https://btc-alpha.com/api/v1/withdraws/",
                "input": []
            }
        ],
        "createOrder": [
            {
                "description": "Spot limit buy",
                "method": "createOrder",
                "url": "https://btc-alpha.com/api/v1/order/",
                "input": [
                    "LTC/USDT",
                    "limit",
                    "buy",
                    0.1,
                    50
                ],
                "output": "amount=0.1&pair=LTC_USDT&price=50&type=buy"
            }
        ],
        "fetchTrades": [
            {
                "description": "spot fetchTrades",
                "method": "fetchTrades",
                "url": "https://btc-alpha.com/api/v1/exchanges/?pair=BTC_USDT",
                "input": [
                    "BTC/USDT"
                ]
            }
        ],
        "fetchOrderBook": [
            {
                "description": "spot orderbook",
                "method": "fetchOrderBook",
                "url": "https://btc-alpha.com/api/v1/orderbook/BTC_USDT",
                "input": [
                    "BTC/USDT"
                ]
            }
        ],
        "fetchTicker": [
            {
                "description": "spot ticker",
                "method": "fetchTicker",
                "url": "https://btc-alpha.com/api/v1/ticker/?pair=BTC_USDT",
                "input": [
                    "BTC/USDT"
                ]
            }
        ],
        "fetchTickers": [
            {
                "description": "spot tickers",
                "method": "fetchTickers",
                "url": "https://btc-alpha.com/api/v1/ticker/",
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
                "url": "https://btc-alpha.com/api/charts/BTC_USDT/5/chart/",
                "input": [
                    "BTC/USDT"
                ]
            }
        ]
    }
}
```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/request/btcalpha.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 155
- Code lines: 155
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
