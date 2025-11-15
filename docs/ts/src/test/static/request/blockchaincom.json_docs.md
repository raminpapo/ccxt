# Documentation: ts/src/test/static/request/blockchaincom.json

## File Metadata

- **Path**: `ts/src/test/static/request/blockchaincom.json`
- **Size**: 4,814 bytes
- **Lines**: 149
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "exchange": "blockchaincom",
    "skipKeys": [
        "clOrdId"
    ],
    "outputType": "json",
    "methods": {
        "fetchMyTrades": [
            {
                "description": "Spot private trades",
                "method": "fetchMyTrades",
                "url": "https://api.blockchain.com/v3/exchange/fills?limit=5&symbol=LTC-USDT",
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
                "url": "https://api.blockchain.com/v3/exchange/orders?status=OPEN&limit=100&symbol=LTC-USDT",
                "input": [
                    "LTC/USDT"
                ]
            }
        ],
        "fetchClosedOrders": [
            {
                "description": "Spot closed orders",
                "method": "fetchClosedOrders",
                "url": "https://api.blockchain.com/v3/exchange/orders?status=FILLED&limit=100&symbol=LTC-USDT",
                "input": [
                    "LTC/USDT"
                ]
            }
        ],
        "cancelAllOrders": [
            {
                "description": "Cancel spot orders",
                "method": "cancelAllOrders",
                "url": "https://api.blockchain.com/v3/exchange/orders",
                "input": [
                    "LTC/USDT"
                ],
                "output": "{\"symbol\":\"LTC-USDT\"}"
            }
        ],
        "fetchBalance": [
            {
                "description": "Fetch spot Balance",
                "method": "fetchBalance",
                "url": "https://api.blockchain.com/v3/exchange/accounts?account=primary&type=spot",
                "input": [
                    {
                        "type": "spot"
                    }
                ]
            },
            {
                "description": "Fetch swap Balance",
                "method": "fetchBalance",
                "url": "https://api.blockchain.com/v3/exchange/accounts?account=primary&type=swap",
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
                "url": "https://api.blockchain.com/v3/exchange/deposits",
                "input": []
            }
        ],
        "fetchWithdrawals": [
            {
                "description": "Fetch withdrawals",
                "method": "fetchWithdrawals",
                "url": "https://api.blockchain.com/v3/exchange/withdrawals",
                "input": []
            }
        ],
        "fetchDepositAddress": [
            {
                "description": "fetch USDT deposit address",
                "method": "fetchDepositAddress",
                "url": "https://api.blockchain.com/v3/exchange/deposits/USDT",
                "input": [
                    "USDT"
                ],
                "output": "{}"
            }
        ],
        "createOrder": [
            {
                "description": "Spot limit buy",
                "method": "createOrder",
                "url": "https://api.blockchain.com/v3/exchange/orders",
                "input": [
                    "LTC/USDT",
                    "limit",
                    "buy",
                    0.1,
                    50
                ],
                "output": "{\"ordType\":\"LIMIT\",\"symbol\":\"LTC-USDT\",\"side\":\"BUY\",\"orderQty\":\"0.1\",\"clOrdId\":\"4314cf84b4d38e68\",\"price\":\"50\"}"
            }
        ],
        "fetchOrderBook": [
            {
                "description": "spot orderbook",
                "method": "fetchOrderBook",
                "url": "https://api.blockchain.com/v3/exchange/l3/BTC-USDT",
                "input": [
                    "BTC/USDT"
                ]
            }
        ],
        "fetchTicker": [
            {
                "description": "spot ticker",
                "method": "fetchTicker",
                "url": "https://api.blockchain.com/v3/exchange/tickers/BTC-USDT",
                "input": [
                    "BTC/USDT"
                ]
            }
        ],
        "fetchTickers": [
            {
                "description": "spot tickers",
                "method": "fetchTickers",
                "url": "https://api.blockchain.com/v3/exchange/tickers",
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

This is a JSON file located at `ts/src/test/static/request/blockchaincom.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 149
- Code lines: 149
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
