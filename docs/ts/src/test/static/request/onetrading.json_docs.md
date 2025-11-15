# Documentation: ts/src/test/static/request/onetrading.json

## File Metadata

- **Path**: `ts/src/test/static/request/onetrading.json`
- **Size**: 3,488 bytes
- **Lines**: 106
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "exchange": "onetrading",
    "skipKeys": [
        "nonce"
    ],
    "outputType": "json",
    "methods": {
        "cancelOrder": [
            {
                "description": "cancel order",
                "method": "cancelOrder",
                "url": "https://api.onetrading.com/fast/v1/account/orders/24b69da8-4bb2-449b-a98a-8fd0f2014552",
                "input": [
                    "24b69da8-4bb2-449b-a98a-8fd0f2014552",
                    "BTC/USDT"
                ],
                "output": null
            }
        ],
        "createOrder": [
            {
                "description": "limit sell order",
                "method": "createOrder",
                "url": "https://api.onetrading.com/fast/v1/account/orders",
                "input": [
                    "BTC/USDT",
                    "limit",
                    "sell",
                    0.0008379,
                    100000
                ],
                "output": "{\"instrument_code\":\"BTC_USDT\",\"type\":\"LIMIT\",\"side\":\"SELL\",\"amount\":\"0.00083\",\"price\":\"100000\",\"time_in_force\":\"GOOD_TILL_CANCELLED\"}"
            }
        ],
        "fetchCurrencies": [
            {
                "description": "fetchCurrencies",
                "method": "fetchCurrencies",
                "url": "https://api.onetrading.com/fast/v1/currencies",
                "input": [],
                "output": null
            },
            {
                "description": "Fetch Currencies",
                "method": "fetchCurrencies",
                "url": "https://api.onetrading.com/fast/v1/currencies",
                "input": []
            }
        ],
        "fetchMarkets": [
            {
                "description": "Fetch Markets",
                "method": "fetchMarkets",
                "url": "https://api.onetrading.com/fast/v1/instruments",
                "input": []
            }
        ],
        "fetchTime": [
            {
                "description": "Fetch Time",
                "method": "fetchTime",
                "url": "https://api.onetrading.com/fast/v1/time",
                "input": []
            }
        ],
        "fetchMyTrades": [
            {
                "description": "fetch my trades",
                "method": "fetchMyTrades",
                "url": "https://api.onetrading.com/fast/v1/account/trades?instrument_code=BTC_USDT",
                "input": [
                  "BTC/USDT"
                ]
            }
        ],
        "fetchBalance": [
            {
                "description": "fetchBalance",
                "method": "fetchBalance",
                "url": "https://api.onetrading.com/fast/v1/account/balances",
                "input": [],
                "output": null
            },
            {
                "description": "Fetch spot Balance",
                "method": "fetchBalance",
                "url": "https://api.onetrading.com/fast/v1/account/balances?type=spot",
                "input": [
                    {
                        "type": "spot"
                    }
                ]
            },
            {
                "description": "Fetch swap Balance",
                "method": "fetchBalance",
                "url": "https://api.onetrading.com/fast/v1/account/balances?type=swap",
                "input": [
                    {
                        "type": "swap"
                    }
                ]
            }
        ]
    }
}
```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/request/onetrading.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 106
- Code lines: 106
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
