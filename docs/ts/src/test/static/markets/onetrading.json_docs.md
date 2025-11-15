# Documentation: ts/src/test/static/markets/onetrading.json

## File Metadata

- **Path**: `ts/src/test/static/markets/onetrading.json`
- **Size**: 8,207 bytes
- **Lines**: 332
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "USDT/EUR": {
        "id": "USDT_EUR",
        "symbol": "USDT/EUR",
        "base": "USDT",
        "quote": "EUR",
        "baseId": "USDT",
        "quoteId": "EUR",
        "type": "spot",
        "spot": true,
        "margin": false,
        "swap": false,
        "future": false,
        "option": false,
        "active": false,
        "contract": false,
        "taker": 0.0015,
        "maker": 0.001,
        "precision": {
            "amount": 0.01,
            "price": 0.00001
        },
        "limits": {
            "leverage": {},
            "amount": {},
            "price": {},
            "cost": {
                "min": 10
            }
        },
        "info": {
            "state": "CLOSED",
            "base": {
                "code": "USDT",
                "precision": "6"
            },
            "quote": {
                "code": "EUR",
                "precision": "2"
            },
            "amount_precision": "2",
            "market_precision": "5",
            "min_size": "10.0"
        },
        "tierBased": true,
        "percentage": true,
        "tiers": [
            {
                "taker": [
                    [
                        0,
                        0.0015
                    ],
                    [
                        100,
                        0.0013
                    ],
                    [
                        250,
                        0.0013
                    ],
                    [
                        1000,
                        0.001
                    ],
                    [
                        5000,
                        0.0009
                    ],
                    [
                        10000,
                        0.00075
                    ],
                    [
                        20000,
                        0.00065
                    ]
                ],
                "maker": [
                    [
                        0,
                        0.001
                    ],
                    [
                        100,
                        0.001
                    ],
                    [
                        250,
                        0.0009
                    ],
                    [
                        1000,
                        0.00075
                    ],
                    [
                        5000,
                        0.0006
                    ],
                    [
                        10000,
                        0.0005
                    ],
                    [
                        20000,
                        0.0005
                    ]
                ]
            }
        ]
    },
    "LTC/EUR": {
        "id": "LTC_EUR",
        "symbol": "LTC/EUR",
        "base": "LTC",
        "quote": "EUR",
        "baseId": "LTC",
        "quoteId": "EUR",
        "type": "spot",
        "spot": true,
        "margin": false,
        "swap": false,
        "future": false,
        "option": false,
        "active": false,
        "contract": false,
        "taker": 0.0015,
        "maker": 0.001,
        "precision": {
            "amount": 0.00001,
            "price": 0.01
        },
        "limits": {
            "leverage": {},
            "amount": {},
            "price": {},
            "cost": {
                "min": 10
            }
        },
        "info": {
            "state": "CLOSED",
            "base": {
                "code": "LTC",
                "precision": "8"
            },
            "quote": {
                "code": "EUR",
                "precision": "2"
            },
            "amount_precision": "5",
            "market_precision": "2",
            "min_size": "10.0"
        },
        "tierBased": true,
        "percentage": true,
        "tiers": [
            {
                "taker": [
                    [
                        0,
                        0.0015
                    ],
                    [
                        100,
                        0.0013
                    ],
                    [
                        250,
                        0.0013
                    ],
                    [
                        1000,
                        0.001
                    ],
                    [
                        5000,
                        0.0009
                    ],
                    [
                        10000,
                        0.00075
                    ],
                    [
                        20000,
                        0.00065
                    ]
                ],
                "maker": [
                    [
                        0,
                        0.001
                    ],
                    [
                        100,
                        0.001
                    ],
                    [
                        250,
                        0.0009
                    ],
                    [
                        1000,
                        0.00075
                    ],
                    [
                        5000,
                        0.0006
                    ],
                    [
                        10000,
                        0.0005
                    ],
                    [
                        20000,
                        0.0005
                    ]
                ]
            }
        ]
    },
    "BTC/USDT": {
        "id": "BTC_USDT",
        "symbol": "BTC/USDT",
        "base": "BTC",
        "quote": "USDT",
        "baseId": "BTC",
        "quoteId": "USDT",
        "type": "spot",
        "spot": true,
        "margin": false,
        "swap": false,
        "future": false,
        "option": false,
        "active": false,
        "contract": false,
        "taker": 0.0015,
        "maker": 0.001,
        "precision": {
            "amount": 0.00001,
            "price": 0.01
        },
        "limits": {
            "leverage": {},
            "amount": {},
            "price": {},
            "cost": {
                "min": 10
            }
        },
        "info": {
            "state": "CLOSED",
            "base": {
                "code": "BTC",
                "precision": "8"
            },
            "quote": {
                "code": "USDT",
                "precision": "6"
            },
            "amount_precision": "5",
            "market_precision": "2",
            "min_size": "10.0"
        },
        "tierBased": true,
        "percentage": true,
        "tiers": [
            {
                "taker": [
                    [
                        0,
                        0.0015
                    ],
                    [
                        100,
                        0.0013
                    ],
                    [
                        250,
                        0.0013
                    ],
                    [
                        1000,
                        0.001
                    ],
                    [
                        5000,
                        0.0009
                    ],
                    [
                        10000,
                        0.00075
                    ],
                    [
                        20000,
                        0.00065
                    ]
                ],
                "maker": [
                    [
                        0,
                        0.001
                    ],
                    [
                        100,
                        0.001
                    ],
                    [
                        250,
                        0.0009
                    ],
                    [
                        1000,
                        0.00075
                    ],
                    [
                        5000,
                        0.0006
                    ],
                    [
                        10000,
                        0.0005
                    ],
                    [
                        20000,
                        0.0005
                    ]
                ]
            }
        ]
    }
}
```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/markets/onetrading.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 332
- Code lines: 332
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
