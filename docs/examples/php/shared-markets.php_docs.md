# Documentation: examples/php/shared-markets.php

## File Metadata

- **Path**: `examples/php/shared-markets.php`
- **Size**: 1,389 bytes
- **Lines**: 55
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

$root = dirname(dirname(dirname(__FILE__)));

include $root . '/ccxt.php';

date_default_timezone_set('UTC');

// ----------------------------------------------------------------------------
// an example of how to load markets for each exchange just once
// in order to save memory and time for initializing multiple exchange instances
// see these issues for details:
// - https://github.com/ccxt/ccxt/issues/7312
// - https://github.com/ccxt/ccxt/issues/8176
// ----------------------------------------------------------------------------

$keys = array(
    'ids',
    'markets',
    'markets_by_id',
    'currencies',
    'currencies_by_id',
    'base_currencies',
    'quote_currencies',
    'symbols',
);


$id = 'kraken';
$exchange_class = "\\ccxt\\{$id}";
$exchange = new $exchange_class();

$markets_on_disk = "./{$id}.markets.json";

$exchange->verbose = true; // this is a debug output to demonstrate which networking calls are being issued

if (file_exists($markets_on_disk)) {

    $cache = json_decode(file_get_contents($markets_on_disk), true);
    foreach ($keys as $key) {
        $exchange->{$key} = $cache[$key];
    }

} else {

    $exchange->load_markets();
    $cache = array();
    foreach ($keys as $key) {
        $cache[$key] = $exchange->{$key};
    }
    file_put_contents($markets_on_disk, json_encode($cache));
}

$exchange->fetch_ticker('ETH/BTC');

```

## High-Level Overview

This is a PHP file located at `examples/php/shared-markets.php`.



## Detailed Walkthrough

### Code Structure

- Total lines: 55
- Code lines: 33
- Comment lines: 7
- Blank lines: 15

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Implements caching mechanisms



## Related Files

- `./{$id}.markets.json` (referenced)
- `/ccxt.php` (referenced)



## Testing & Execution

**To execute this PHP file:**

```bash
php examples/php/shared-markets.php
```

