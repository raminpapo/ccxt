# Documentation: examples/php/cache-exchange-instance-reuse.php

## File Metadata

- **Path**: `examples/php/cache-exchange-instance-reuse.php`
- **Size**: 1,118 bytes
- **Lines**: 29
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

error_reporting(E_ALL);
date_default_timezone_set('UTC');

include dirname(dirname(dirname(__FILE__))) . '/ccxt.php';

function create_exchange($exchange_id, $config) {

    $exchange_class = '\\ccxt\\' . $exchange_id;
    $exchange = new $exchange_class($config);
    $cache_location = "./cached_{$exchange_id}_data.json";
    $start_time = microtime(true);

    if (file_exists($cache_location)) {
        $loaded_cache = json_decode(file_get_contents($cache_location), true);
        $exchange->set_markets($loaded_cache['markets'], $loaded_cache['currencies']);
        print("{$exchange_id} Loaded markets from cache in " . (microtime(true) - $start_time) . " seconds\n");
    } else {
        $markets = $exchange->load_markets();
        file_put_contents($cache_location, json_encode(['markets'=>$markets, 'currencies'=>$exchange->currencies]));
        print("{$exchange_id} Loaded fresh markets in " . (microtime(true) - $start_time) . " seconds\n");
    }
    return $exchange;
}

$exchange1 = create_exchange('bittrex', ['custom_id'=>'mybittrex1']);
print ($exchange1->fetch_trades('BTC/USDT')[0]);

```

## High-Level Overview

This is a PHP file located at `examples/php/cache-exchange-instance-reuse.php`.

**Functions defined**: create_exchange



## Detailed Walkthrough

### Code Structure

- Total lines: 29
- Code lines: 22
- Comment lines: 0
- Blank lines: 7

### Main Components

**Functions** (1):
- `create_exchange()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

### Performance Notes

- ✓ Implements caching mechanisms



## Related Files

- ` . (microtime(true) - $start_time) . ` (imported)
- `./cached_{$exchange_id}_data.json` (referenced)
- `/ccxt.php` (referenced)



## Testing & Execution

**To execute this PHP file:**

```bash
php examples/php/cache-exchange-instance-reuse.php
```

