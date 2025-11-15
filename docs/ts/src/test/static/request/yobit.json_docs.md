# Documentation: ts/src/test/static/request/yobit.json

## File Metadata

- **Path**: `ts/src/test/static/request/yobit.json`
- **Size**: 4,083 bytes
- **Lines**: 133
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "exchange": "yobit",
    "skipKeys": [
        "nonce",
        "since"
    ],
    "outputType": "both",
    "methods": {
        "createOrder": [
            {
                "description": "create limit order",
                "method": "createOrder",
                "url": "https://yobit.net/tapi",
                "input": [
                    "DOGE/USDT",
                    "limit",
                    "buy",
                    10,
                    0.15
                ],
                "output": "nonce=1709814297&method=Trade&pair=doge_usdt&type=buy&amount=10&rate=0.15"
            }
        ],
        "fetchMyTrades": [
            {
                "description": "Spot private trades",
                "method": "fetchMyTrades",
                "url": "https://yobit.net/tapi",
                "input": [
                    "LTC/USDT",
                    1699457638000,
                    5
                ],
                "output": "nonce=1709813589&method=TradeHistory&pair=ltc_usdt&count=5&since=1699457638"
            }
        ],
        "fetchBalance": [
            {
                "description": "fetch balance",
                "method": "fetchBalance",
                "url": "https://yobit.net/tapi",
                "input": [],
                "output": "nonce=1709813620&method=getInfo"
            }
        ],
        "fetchTrades": [
            {
                "description": "spot trades",
                "method": "fetchTrades",
                "url": "https://yobit.net/api/3/trades/ltc_usdt",
                "input": [
                    "LTC/USDT"
                ]
            },
            {
                "description": "spot fetchTrades",
                "method": "fetchTrades",
                "url": "https://yobit.net/api/3/trades/btc_usdt",
                "input": [
                    "BTC/USDT"
                ]
            }
        ],
        "fetchOpenOrders": [
            {
                "description": "open orders",
                "method": "fetchOpenOrders",
                "url": "https://yobit.net/tapi",
                "input": [
                    "LTC/USDT"
                ],
                "output": "nonce=1709813728&method=ActiveOrders&pair=ltc_usdt"
            }
        ],
        "fetchOrder": [
            {
                "description": "fetch order",
                "method": "fetchOrder",
                "url": "https://yobit.net/tapi",
                "input": [
                    1101104080583007,
                    "DOGE/USDT"
                ],
                "output": "nonce=1709814336&method=OrderInfo&order_id=1101104080583007"
            }
        ],
        "cancelOrder": [
            {
                "description": "cancel order",
                "method": "cancelOrder",
                "url": "https://yobit.net/tapi",
                "input": [
                    1101104080583007,
                    "DOGE/USDT"
                ],
                "output": "nonce=1709814369&method=CancelOrder&order_id=1101104080583007"
            }
        ],
        "fetchOrderBook": [
            {
                "description": "spot orderbook",
                "method": "fetchOrderBook",
                "url": "https://yobit.net/api/3/depth/btc_usdt",
                "input": [
                    "BTC/USDT"
                ]
            }
        ],
        "fetchTicker": [
            {
                "description": "spot ticker",
                "method": "fetchTicker",
                "url": "https://yobit.net/api/3/ticker/btc_usdt",
                "input": [
                    "BTC/USDT"
                ]
            }
        ],
        "fetchTickers": [
            {
                "description": "spot tickers",
                "method": "fetchTickers",
                "url": "https://yobit.net/api/3/ticker/btc_usdt-eth_usdt",
                "input": [
                    [
                        "BTC/USDT",
                        "ETH/USDT"
                    ]
                ]
            }
        ]
    }
}
```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/request/yobit.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 133
- Code lines: 133
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
