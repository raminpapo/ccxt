# Documentation: ts/src/test/static/request/bit2c.json

## File Metadata

- **Path**: `ts/src/test/static/request/bit2c.json`
- **Size**: 2,227 bytes
- **Lines**: 71
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "exchange": "bit2c",
    "skipKeys": [
        "nonce"
    ],
    "outputType": "urlencoded",
    "methods": {
        "fetchTrades": [
            {
                "description": "fetchTrades",
                "method": "fetchTrades",
                "url": "https://bit2c.co.il/Exchanges/BtcNis/trades.json",
                "input": [
                    "BTC/NIS"
                ]
            }
        ],
        "createOrder": [
            {
                "description": "createOrder",
                "method": "createOrder",
                "url": "https://bit2c.co.il/Order/AddOrderMarketPriceBuy",
                "input": [
                    "BTC/NIS",
                    "market",
                    "buy",
                    1
                ],
                "output": "nonce=1702456164084&Amount=1&Pair=BtcNis"
            },
            {
                "description": "createOrder",
                "method": "createOrder",
                "url": "https://bit2c.co.il/Order/AddOrderMarketPriceSell",
                "input": [
                    "BTC/NIS",
                    "market",
                    "sell",
                    1
                ],
                "output": "nonce=1702456164084&Amount=1&Pair=BtcNis"
            },
            {
                "description": "createOrder",
                "method": "createOrder",
                "url": "https://bit2c.co.il/Order/AddOrder",
                "input": [
                    "BTC/NIS",
                    "limit",
                    "buy",
                    1,
                    154827
                ],
                "output": "nonce=1702456292767&Amount=1&Pair=BtcNis&Price=154827&Total=154827&IsBid=true"
            },
            {
                "description": "createOrder",
                "method": "createOrder",
                "url": "https://bit2c.co.il/Order/AddOrder",
                "input": [
                    "BTC/NIS",
                    "limit",
                    "sell",
                    1,
                    154827
                ],
                "output": "nonce=1702456292767&Amount=1&Pair=BtcNis&Price=154827&Total=154827&IsBid=false"
            }
        ]
    }
}
```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/request/bit2c.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 71
- Code lines: 71
- Comment lines: 0
- Blank lines: 0

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `https://bit2c.co.il/Exchanges/BtcNis/trades.json` (referenced)



## Testing & Execution

This appears to be a test file.

**To run this test:**
