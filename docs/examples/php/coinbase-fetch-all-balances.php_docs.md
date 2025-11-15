# Documentation: examples/php/coinbase-fetch-all-balances.php

## File Metadata

- **Path**: `examples/php/coinbase-fetch-all-balances.php`
- **Size**: 1,111 bytes
- **Lines**: 42
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

$root = dirname(dirname(dirname(__FILE__)));

include $root . '/ccxt.php';

date_default_timezone_set('UTC');

$exchange = new \ccxt\coinbase(array(
    'apiKey' => 'YOUR_API_KEY',
    'secret' => 'YOUR_SECRET',
    // 'verbose' => true, // uncomment for debugging
));

$exchange->load_markets();

// $exchange->verbose = true; // uncomment for debugging

$result = array();
$params = array();
$loop = true;
do {
    $balance = $exchange->fetch_balance($params);
    $pagination = $exchange->safe_value($balance['info'], 'pagination');
    if ($pagination === null) {
        $loop = false;
    } else {
        $next_starting_after = $exchange->safe_string ($pagination, 'next_starting_after');
        if ($next_starting_after !== null) {
            $params['starting_after'] = $next_starting_after;
        } else {
            $loop = false;
        }
    }
    echo $exchange->iso8601($exchange->milliseconds()) . "\n";
    $result = $exchange->deep_extend($result, $balance);
} while ($loop);

echo "======================================================================\n";
var_dump($result);

?>
```

## High-Level Overview

This is a PHP file located at `examples/php/coinbase-fetch-all-balances.php`.



## Detailed Walkthrough

### Code Structure

- Total lines: 42
- Code lines: 31
- Comment lines: 2
- Blank lines: 9

### Main Components



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

- `/ccxt.php` (referenced)



## Testing & Execution

**To execute this PHP file:**

```bash
php examples/php/coinbase-fetch-all-balances.php
```

