# Documentation: ts/src/test/static/currencies/gemini.json

## File Metadata

- **Path**: `ts/src/test/static/currencies/gemini.json`
- **Size**: 11,217 bytes
- **Lines**: 482
- **Type**: JSON
- **Extension**: .json


## Original Source Code

```json
{
    "BTC": {
        "info": [
            "BTC",
            "Bitcoin",
            1,
            8,
            0,
            8,
            8,
            false,
            null,
            "bitcoin"
        ],
        "id": "BTC",
        "numericId": null,
        "code": "BTC",
        "precision": 1e-8,
        "type": "fiat",
        "name": "Bitcoin",
        "active": null,
        "deposit": null,
        "withdraw": null,
        "fee": null,
        "fees": {},
        "networks": {
            "BTC": {
                "info": [
                    "BTC",
                    "Bitcoin",
                    1,
                    8,
                    0,
                    8,
                    8,
                    false,
                    null,
                    "bitcoin"
                ],
                "id": "bitcoin",
                "network": "BTC",
                "active": null,
                "deposit": null,
                "withdraw": null,
                "fee": null,
                "precision": 1e-8,
                "limits": {
                    "deposit": {
                        "min": null,
                        "max": null
                    },
                    "withdraw": {
                        "min": null,
                        "max": null
                    }
                }
            }
        },
        "limits": {
            "deposit": {
                "min": null,
                "max": null
            },
            "withdraw": {
                "min": null,
                "max": null
            }
        }
    },
    "USDT": {
        "info": [
            "USDT",
            "Tether",
            50,
            6,
            0,
            6,
            8,
            false,
            null,
            "ethereum"
        ],
        "id": "USDT",
        "numericId": null,
        "code": "USDT",
        "precision": 0.000001,
        "type": "fiat",
        "name": "Tether",
        "active": null,
        "deposit": null,
        "withdraw": null,
        "fee": null,
        "fees": {},
        "networks": {
            "ERC20": {
                "info": [
                    "USDT",
                    "Tether",
                    50,
                    6,
                    0,
                    6,
                    8,
                    false,
                    null,
                    "ethereum"
                ],
                "id": "ethereum",
                "network": "ERC20",
                "active": null,
                "deposit": null,
                "withdraw": null,
                "fee": null,
                "precision": 0.000001,
                "limits": {
                    "deposit": {
                        "min": null,
                        "max": null
                    },
                    "withdraw": {
                        "min": null,
                        "max": null
                    }
                }
            }
        },
        "limits": {
            "deposit": {
                "min": null,
                "max": null
            },
            "withdraw": {
                "min": null,
                "max": null
            }
        }
    },
    "EUR": {
        "info": [
            "EUR",
            "Euro",
            21,
            2,
            2,
            2,
            2,
            true,
            "€",
            null
        ],
        "id": "EUR",
        "numericId": null,
        "code": "EUR",
        "precision": 0.01,
        "type": "fiat",
        "name": "Euro",
        "active": null,
        "deposit": null,
        "withdraw": null,
        "fee": null,
        "fees": {},
        "networks": {},
        "limits": {
            "deposit": {
                "min": null,
                "max": null
            },
            "withdraw": {
                "min": null,
                "max": null
            }
        }
    },
    "USD": {
        "info": [
            "USD",
            "U.S. Dollar",
            0,
            2,
            2,
            2,
            2,
            true,
            "$",
            null
        ],
        "id": "USD",
        "numericId": null,
        "code": "USD",
        "precision": 0.01,
        "type": "fiat",
        "name": "U.S. Dollar",
        "active": null,
        "deposit": null,
        "withdraw": null,
        "fee": null,
        "fees": {},
        "networks": {},
        "limits": {
            "deposit": {
                "min": null,
                "max": null
            },
            "withdraw": {
                "min": null,
                "max": null
            }
        }
    },
    "LTC": {
        "info": [
            "LTC",
            "Litecoin",
            4,
            6,
            0,
            8,
            8,
            false,
            "Ł",
            "litecoin"
        ],
        "id": "LTC",
        "numericId": null,
        "code": "LTC",
        "precision": 1e-8,
        "type": "fiat",
        "name": "Litecoin",
        "active": null,
        "deposit": null,
        "withdraw": null,
        "fee": null,
        "fees": {},
        "networks": {
            "LTC": {
                "info": [
                    "LTC",
                    "Litecoin",
                    4,
                    6,
                    0,
                    8,
                    8,
                    false,
                    "Ł",
                    "litecoin"
                ],
                "id": "litecoin",
                "network": "LTC",
                "active": null,
                "deposit": null,
                "withdraw": null,
                "fee": null,
                "precision": 1e-8,
                "limits": {
                    "deposit": {
                        "min": null,
                        "max": null
                    },
                    "withdraw": {
                        "min": null,
                        "max": null
                    }
                }
            }
        },
        "limits": {
            "deposit": {
                "min": null,
                "max": null
            },
            "withdraw": {
                "min": null,
                "max": null
            }
        }
    },
    "ETH": {
        "info": [
            "ETH",
            "Ether",
            2,
            6,
            0,
            18,
            8,
            false,
            null,
            "ethereum"
        ],
        "id": "ETH",
        "numericId": null,
        "code": "ETH",
        "precision": 1e-18,
        "type": "fiat",
        "name": "Ether",
        "active": null,
        "deposit": null,
        "withdraw": null,
        "fee": null,
        "fees": {},
        "networks": {
            "ERC20": {
                "info": [
                    "ETH",
                    "Ether",
                    2,
                    6,
                    0,
                    18,
                    8,
                    false,
                    null,
                    "ethereum"
                ],
                "id": "ethereum",
                "network": "ERC20",
                "active": null,
                "deposit": null,
                "withdraw": null,
                "fee": null,
                "precision": 1e-18,
                "limits": {
                    "deposit": {
                        "min": null,
                        "max": null
                    },
                    "withdraw": {
                        "min": null,
                        "max": null
                    }
                }
            }
        },
        "limits": {
            "deposit": {
                "min": null,
                "max": null
            },
            "withdraw": {
                "min": null,
                "max": null
            }
        }
    },
    "XRP": {
        "info": [
            "XRP",
            "XRP",
            47,
            6,
            0,
            6,
            8,
            false,
            null,
            "xrpl"
        ],
        "id": "XRP",
        "numericId": null,
        "code": "XRP",
        "precision": 0.000001,
        "type": "fiat",
        "name": "XRP",
        "active": null,
        "deposit": null,
        "withdraw": null,
        "fee": null,
        "fees": {},
        "networks": {
            "xrpl": {
                "info": [
                    "XRP",
                    "XRP",
                    47,
                    6,
                    0,
                    6,
                    8,
                    false,
                    null,
                    "xrpl"
                ],
                "id": "xrpl",
                "network": "xrpl",
                "active": null,
                "deposit": null,
                "withdraw": null,
                "fee": null,
                "precision": 0.000001,
                "limits": {
                    "deposit": {
                        "min": null,
                        "max": null
                    },
                    "withdraw": {
                        "min": null,
                        "max": null
                    }
                }
            }
        },
        "limits": {
            "deposit": {
                "min": null,
                "max": null
            },
            "withdraw": {
                "min": null,
                "max": null
            }
        }
    },
    "USDC": {
        "info": [
            "USDC",
            "USD Coin",
            39,
            6,
            0,
            6,
            8,
            false,
            null,
            "ethereum"
        ],
        "id": "USDC",
        "numericId": null,
        "code": "USDC",
        "precision": 0.000001,
        "type": "fiat",
        "name": "USD Coin",
        "active": null,
        "deposit": null,
        "withdraw": null,
        "fee": null,
        "fees": {},
        "networks": {
            "ERC20": {
                "info": [
                    "USDC",
                    "USD Coin",
                    39,
                    6,
                    0,
                    6,
                    8,
                    false,
                    null,
                    "ethereum"
                ],
                "id": "ethereum",
                "network": "ERC20",
                "active": null,
                "deposit": null,
                "withdraw": null,
                "fee": null,
                "precision": 0.000001,
                "limits": {
                    "deposit": {
                        "min": null,
                        "max": null
                    },
                    "withdraw": {
                        "min": null,
                        "max": null
                    }
                }
            }
        },
        "limits": {
            "deposit": {
                "min": null,
                "max": null
            },
            "withdraw": {
                "min": null,
                "max": null
            }
        }
    }
}
```

## High-Level Overview

This is a JSON file located at `ts/src/test/static/currencies/gemini.json`.



## Detailed Walkthrough

### Code Structure

- Total lines: 482
- Code lines: 482
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
