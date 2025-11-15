# Documentation: ts/src/test/static/request/bequant.json

## File Metadata

- **Path**: `ts/src/test/static/request/bequant.json`
- **Size**: 2,975 bytes
- **Lines**: 93
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "exchange": "bequant",
    "skipKeys": [],
    "outputType": "json",
    "methods": {
        "fetchMyTrades": [
            {
                "description": "Spot private trades ",
                "method": "fetchMyTrades",
                "url": "https://api.bequant.io/api/3/spot/history/trade?symbol=LTCUSDT&limit=5&from=1699457638000",
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
                "url": "https://api.bequant.io/api/3/spot/order?symbol=LTCUSDT",
                "input": [
                    "LTC/USDT"
                ]
            }
        ],
        "fetchClosedOrders": [
            {
                "description": "Spot closed orders",
                "method": "fetchClosedOrders",
                "url": "https://api.bequant.io/api/3/spot/history/order?symbol=LTCUSDT",
                "input": [
                    "LTC/USDT"
                ]
            }
        ],
        "cancelAllOrders": [
            {
                "description": "Cancel spot orders",
                "method": "cancelAllOrders",
                "url": "https://api.bequant.io/api/3/spot/order",
                "input": [
                    "LTC/USDT"
                ],
                "output": "{\"symbol\":\"LTCUSDT\"}"
            }
        ],
        "fetchBalance": [
            {
                "description": "Fetch spot Balance",
                "method": "fetchBalance",
                "url": "https://api.bequant.io/api/3/spot/balance",
                "input": [
                    {
                        "type": "spot"
                    }
                ]
            }
        ],
        "fetchDeposits": [
            {
                "description": "Fetch deposits",
                "method": "fetchDeposits",
                "url": "https://api.bequant.io/api/3/wallet/transactions?types=DEPOSIT",
                "input": []
            }
        ],
        "fetchWithdrawals": [
            {
                "description": "Fetch withdrawals",
                "method": "fetchWithdrawals",
                "url": "https://api.bequant.io/api/3/wallet/transactions?types=WITHDRAW",
                "input": []
            }
        ],
        "createOrder": [
            {
                "description": "Spot limit buy",
                "method": "createOrder",
                "url": "https://api.bequant.io/api/3/spot/order",
                "input": [
                    "LTC/USDT",
                    "limit",
                    "buy",
                    0.1,
                    50
                ],
                "output": "{\"type\":\"limit\",\"side\":\"buy\",\"quantity\":\"0.1\",\"symbol\":\"LTCUSDT\",\"price\":\"50\"}"
            }
        ]
    }
}
```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/request/bequant.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 93
- Code lines: 93
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
