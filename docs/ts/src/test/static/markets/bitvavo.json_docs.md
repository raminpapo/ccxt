# Documentation: ts/src/test/static/markets/bitvavo.json

## File Metadata

- **Path**: `ts/src/test/static/markets/bitvavo.json`
- **Size**: 7,973 bytes
- **Lines**: 326
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "BTC/EUR": {
        "id": "BTC-EUR",
        "lowercaseId": null,
        "symbol": "BTC/EUR",
        "base": "BTC",
        "quote": "EUR",
        "settle": null,
        "baseId": "BTC",
        "quoteId": "EUR",
        "settleId": null,
        "type": "spot",
        "spot": true,
        "margin": false,
        "swap": false,
        "future": false,
        "option": false,
        "index": false,
        "active": true,
        "contract": false,
        "linear": null,
        "inverse": null,
        "subType": null,
        "taker": 0.0025,
        "maker": 0.002,
        "contractSize": null,
        "expiry": null,
        "expiryDatetime": null,
        "strike": null,
        "optionType": null,
        "precision": {
            "amount": 1e-8,
            "price": 1,
            "cost": 0.01
        },
        "limits": {
            "leverage": {
                "min": null,
                "max": null
            },
            "amount": {
                "min": 0.000061,
                "max": 1000000000
            },
            "price": {
                "min": null,
                "max": null
            },
            "cost": {
                "min": 5,
                "max": 1000000000
            }
        },
        "marginModes": {
            "cross": null,
            "isolated": null
        },
        "created": null,
        "info": {
            "market": "BTC-EUR",
            "status": "trading",
            "base": "BTC",
            "quote": "EUR",
            "pricePrecision": "0",
            "minOrderInBaseAsset": "0.00006100",
            "minOrderInQuoteAsset": "5.00",
            "maxOrderInBaseAsset": "1000000000.00000000",
            "maxOrderInQuoteAsset": "1000000000.00",
            "quantityDecimals": "8",
            "notionalDecimals": "2",
            "tickSize": "1.00",
            "maxOpenOrders": "100",
            "feeCategory": "A",
            "orderTypes": [
                "market",
                "limit",
                "stopLoss",
                "stopLossLimit",
                "takeProfit",
                "takeProfitLimit"
            ]
        },
        "tierBased": true,
        "percentage": true,
        "tiers": {
            "taker": [
                [
                    0,
                    0.0025
                ],
                [
                    100000,
                    0.002
                ],
                [
                    250000,
                    0.0016
                ],
                [
                    500000,
                    0.0012
                ],
                [
                    1000000,
                    0.001
                ],
                [
                    2500000,
                    0.0008
                ],
                [
                    5000000,
                    0.0006
                ],
                [
                    10000000,
                    0.0005
                ],
                [
                    25000000,
                    0.0004
                ]
            ],
            "maker": [
                [
                    0,
                    0.0015
                ],
                [
                    100000,
                    0.001
                ],
                [
                    250000,
                    0.0008
                ],
                [
                    500000,
                    0.0006
                ],
                [
                    1000000,
                    0.0005
                ],
                [
                    2500000,
                    0.0004
                ],
                [
                    5000000,
                    0.0004
                ],
                [
                    10000000,
                    0.0003
                ],
                [
                    25000000,
                    0.0003
                ]
            ]
        }
    },
    "LTC/EUR": {
        "id": "LTC-EUR",
        "lowercaseId": null,
        "symbol": "LTC/EUR",
        "base": "LTC",
        "quote": "EUR",
        "settle": null,
        "baseId": "LTC",
        "quoteId": "EUR",
        "settleId": null,
        "type": "spot",
        "spot": true,
        "margin": false,
        "swap": false,
        "future": false,
        "option": false,
        "index": false,
        "active": true,
        "contract": false,
        "linear": null,
        "inverse": null,
        "subType": null,
        "taker": 0.0025,
        "maker": 0.002,
        "contractSize": null,
        "expiry": null,
        "expiryDatetime": null,
        "strike": null,
        "optionType": null,
        "precision": {
            "amount": 1e-8,
            "price": 0.001,
            "cost": 0.01
        },
        "limits": {
            "leverage": {
                "min": null,
                "max": null
            },
            "amount": {
                "min": 0.06,
                "max": 1000000000
            },
            "price": {
                "min": null,
                "max": null
            },
            "cost": {
                "min": 5,
                "max": 1000000000
            }
        },
        "marginModes": {
            "cross": null,
            "isolated": null
        },
        "created": null,
        "info": {
            "market": "LTC-EUR",
            "status": "trading",
            "base": "LTC",
            "quote": "EUR",
            "pricePrecision": "0",
            "minOrderInBaseAsset": "0.06000000",
            "minOrderInQuoteAsset": "5.00",
            "maxOrderInBaseAsset": "1000000000.00000000",
            "maxOrderInQuoteAsset": "1000000000.00",
            "quantityDecimals": "8",
            "notionalDecimals": "2",
            "tickSize": "0.00100",
            "maxOpenOrders": "100",
            "feeCategory": "A",
            "orderTypes": [
                "market",
                "limit",
                "stopLoss",
                "stopLossLimit",
                "takeProfit",
                "takeProfitLimit"
            ]
        },
        "tierBased": true,
        "percentage": true,
        "tiers": {
            "taker": [
                [
                    0,
                    0.0025
                ],
                [
                    100000,
                    0.002
                ],
                [
                    250000,
                    0.0016
                ],
                [
                    500000,
                    0.0012
                ],
                [
                    1000000,
                    0.001
                ],
                [
                    2500000,
                    0.0008
                ],
                [
                    5000000,
                    0.0006
                ],
                [
                    10000000,
                    0.0005
                ],
                [
                    25000000,
                    0.0004
                ]
            ],
            "maker": [
                [
                    0,
                    0.0015
                ],
                [
                    100000,
                    0.001
                ],
                [
                    250000,
                    0.0008
                ],
                [
                    500000,
                    0.0006
                ],
                [
                    1000000,
                    0.0005
                ],
                [
                    2500000,
                    0.0004
                ],
                [
                    5000000,
                    0.0004
                ],
                [
                    10000000,
                    0.0003
                ],
                [
                    25000000,
                    0.0003
                ]
            ]
        }
    }
}
```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/markets/bitvavo.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 326
- Code lines: 326
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
