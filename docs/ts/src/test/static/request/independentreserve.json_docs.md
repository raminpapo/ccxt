# Documentation: ts/src/test/static/request/independentreserve.json

## File Metadata

- **Path**: `ts/src/test/static/request/independentreserve.json`
- **Size**: 2,746 bytes
- **Lines**: 64
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "exchange": "independentreserve",
    "skipKeys": [
        "apiKey",
        "nonce",
        "signature"
    ],
    "outputType": "json",
    "methods": {
        "createOrder": [
            {
                "description": "market buy",
                "method": "createOrder",
                "url": "https://api.independentreserve.com/Private/PlaceMarketOrder",
                "input": [
                    "BTC/USD",
                    "market",
                    "buy",
                    0.1
                ],
                "output": "{\"apiKey\":\"key\",\"nonce\":1704966791,\"signature\":\"4125F18EEBC077BDB02DA1FB95D3499842183986F9A20927F3125F611A1ACA61\",\"primaryCurrencyCode\":\"Xbt\",\"secondaryCurrencyCode\":\"Usd\",\"orderType\":\"MarketBid\",\"volume\":0.1}"
            },
            {
                "description": "limit buy",
                "method": "createOrder",
                "url": "https://api.independentreserve.com/Private/PlaceLimitOrder",
                "input": [
                    "BTC/USD",
                    "limit",
                    "buy",
                    0.1,
                    44000
                ],
                "output": "{\"apiKey\":\"key\",\"nonce\":1704966791,\"signature\":\"4125F18EEBC077BDB02DA1FB95D3499842183986F9A20927F3125F611A1ACA61\",\"primaryCurrencyCode\":\"Xbt\",\"secondaryCurrencyCode\":\"Usd\",\"orderType\":\"LimitBid\",\"volume\":0.1,\"price\":44000}"
            }
        ],
        "fetchDepositAddress": [
            {
                "description": "Fetch Deposit Address",
                "method": "fetchDepositAddress",
                "url": "https://api.independentreserve.com/Private/GetDigitalCurrencyDepositAddress",
                "input": [
                  "BTC"
                ],
                "output": "{\"apiKey\":\"key\",\"nonce\":1708428106,\"signature\":\"4125F18EEBC077BDB02DA1FB95D3499842183986F9A20927F3125F611A1ACA61\",\"primaryCurrencyCode\":\"Xbt\"}"
            }
        ],
        "withdraw": [
            {
                "description": "Withdraw",
                "method": "withdraw",
                "url": "https://api.independentreserve.com/Private/WithdrawDigitalCurrency",
                "input": [
                  "XRP",
                  35.03221,
                  "rs2dgzYeqYqsk8bvkQR5YPyqsXYcA24MP2",
                  "376382"
                ],
                "output": "{\"apiKey\":\"23974850e-39kd-393d-393d-12038540\",\"nonce\":1721298323,\"signature\":\"AALSDKJFLKJEKLJLKJLKAWJLKJJLKASJLDKGJALSKDJ\",\"primaryCurrencyCode\":\"Xrp\",\"withdrawalAddress\":\"rs2dgzYeqYqsk8bvkQR5YPyqsXYcA24MP2\",\"amount\":\"35.03221\",\"destinationTag\":\"376382\"}"
            }
        ]
    }
}

```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/request/independentreserve.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 64
- Code lines: 63
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
