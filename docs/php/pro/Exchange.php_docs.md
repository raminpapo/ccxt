# Documentation: php/pro/Exchange.php

## File Metadata

- **Path**: `php/pro/Exchange.php`
- **Size**: 1,557 bytes
- **Lines**: 99
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

namespace ccxt\pro;

// rounding mode duplicated from CCXT
// const TRUNCATE = 0;
// const ROUND = 1;
// const ROUND_UP = 2;
// const ROUND_DOWN = 3;

class Exchange extends \ccxt\async\Exchange {

    use ClientTrait;

    public static $exchanges = array();
}

// the override below is technically an error
// todo: fix the conflict of ccxt.exchanges vs ccxtpro.exchanges

Exchange::$exchanges = array(
    'alpaca',
    'apex',
    'arkham',
    'ascendex',
    'backpack',
    'bequant',
    'binance',
    'binancecoinm',
    'binanceus',
    'binanceusdm',
    'bingx',
    'bitfinex',
    'bitget',
    'bithumb',
    'bitmart',
    'bitmex',
    'bitopro',
    'bitrue',
    'bitstamp',
    'bittrade',
    'bitvavo',
    'blockchaincom',
    'blofin',
    'bybit',
    'cex',
    'coinbase',
    'coinbaseadvanced',
    'coinbaseexchange',
    'coinbaseinternational',
    'coincatch',
    'coincheck',
    'coinex',
    'coinone',
    'cryptocom',
    'deepcoin',
    'defx',
    'deribit',
    'derive',
    'dydx',
    'exmo',
    'gate',
    'gateio',
    'gemini',
    'hashkey',
    'hitbtc',
    'hollaex',
    'htx',
    'huobi',
    'hyperliquid',
    'independentreserve',
    'kraken',
    'krakenfutures',
    'kucoin',
    'kucoinfutures',
    'lbank',
    'luno',
    'mexc',
    'modetrade',
    'myokx',
    'ndax',
    'okx',
    'okxus',
    'onetrading',
    'oxfun',
    'p2b',
    'paradex',
    'phemex',
    'poloniex',
    'probit',
    'toobit',
    'upbit',
    'whitebit',
    'woo',
    'woofipro',
    'xt',
);


```

## High-Level Overview

This is a PHP file located at `php/pro/Exchange.php`.

**Classes defined**: Exchange



## Detailed Walkthrough

### Code Structure

- Total lines: 99
- Code lines: 83
- Comment lines: 7
- Blank lines: 9

### Main Components

**Constants** (4):
- `ROUND`
- `ROUND_DOWN`
- `ROUND_UP`
- `TRUNCATE`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/pro/Exchange.php
```

